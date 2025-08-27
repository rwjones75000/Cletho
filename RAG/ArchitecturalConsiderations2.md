# 250827 – Architectural Note: Cletho’s Minimum Viable RAG System

This document captures the principal architectural features of the RAG system for Cletho, as of late August 2025. It is written so that if all prior documentation is lost, a future reader (human or AI) will still understand the reasoning and design intent.

---

## Purpose

Cletho is a decision assistant designed to help users make complex decisions through a structured, multi-step dialogue. That dialogue consists primarily of Cletho asking the user questions in order to (1) build out a decision matrix, and (2) identify any cognitive biases that may be affecting the user’s reasoning.

To support this, Cletho requires a **retrieval-augmented generation (RAG) system**.   

Unlike most RAG systems, which are designed to answer **user-prompted questions**, Cletho’s variant must also support **system-initiated prompts** that emerge from scripted steps in a decision-making and bias-identification framework.

---

## Retrieval Triggers

Cletho’s RAG is **dual-triggered**:

1. **Script-originated events**  
   Retrieval may be triggered from Cletho’s internal scripts, for example:  
   - When a step calls for a **definition or explanation**  
   - When a worked **example** or template is useful  
   - When Cletho needs to surface **heuristics or bias checks**

2. **User-originated input**  
   Retrieval may also be triggered by **any form of user input**, not just explicit questions. Examples:  
   - A direct **question**: *“What’s expected utility?”*  
   - An **answer** to Cletho’s question: *“My options are keep job, take startup offer, do sabbatical.”*  
   - A **statement or reflection**: *“I’m worried anchoring is affecting me here.”*

This design means the retrieval system is not reactive alone — it is woven into the procedural flow of Cletho’s dialogue.

---   

## Dual Data Flows in Cletho’s MVP RAG

Cletho’s architecture must handle **two distinct but connected data flows**:

1. **User-Originated Flow** — when the user initiates with a question, answer, or statement.  
2. **System-Originated Flow** — when Cletho initiates with a scripted question, sometimes augmented with retrieval.  

These flows differ in **where the retrieval trigger decision happens**:  
- In the **user flow**, the **classifier** decides whether to invoke RAG.  
- In the **system flow**, the **script engine** decides based on RAG hooks embedded in the decision cycle steps.  

Both flows converge after Cletho delivers a prompt and the user responds, ensuring a consistent pipeline.

---

| **User-Originated Flow** | **System-Originated Flow (Cletho-Asks)** |
|--------------------------|-------------------------------------------|
| 1. **User Input** → User asks a question, gives an answer, or makes a statement. | 1. **Script Engine** → Advances to the next Decision Cycle Step. May include an explicit RAG hook. |
| 2. **Classifier** → Labels the turn (`question`, `answer`, `statement`) and decides whether retrieval is needed. | 2. **Trigger Decision** → If the step has a RAG hook, retrieval is triggered automatically. Otherwise, Cletho just asks the scripted question. |
| 3. **Query Builder** → If retrieval is triggered, constructs a query from current turn + step metadata + session summary. | 3. **Query Builder** → If retrieval is triggered, constructs a query from script prompt + step metadata + session summary. |
| 4. **Retriever** → Runs hybrid search (keyword, semantic, metadata) in Supabase (KB + session summaries). | 4. **Retriever** → Same hybrid search, but based on the script’s need. |
| 5. **LLM Wrapper** → Generates a cite-aware response (answer, definition, bias check). | 5. **LLM Wrapper** → Generates a cite-aware augmentation of Cletho’s scripted prompt (definition, example, scaffold). |
| 6. **Response Delivery** → Cletho replies to user. | 6. **Prompt Delivery** → Cletho poses the question (script + augmented content) to the user. |
| 7. **Update State** → Logs retrieval, updates session summary, stores artifacts. | 7. **User Responds** → Which kicks the flow back into the *User-Originated* pipeline. |

---

### Key Takeaways
- Cletho runs on **two alternating flows**: user-driven and system-driven.  
- **Retrieval triggers** differ: the **classifier** governs user turns; the **script engine** governs Cletho’s own turns.  
- After Cletho delivers a scripted prompt, the system always transitions back into the **user-originated flow**, keeping the architecture unified.


---

## Query Construction

Retrieval queries are **not formed from raw user turns alone.** Instead, they are constructed from a blend of:

- **Current turn text** (from user or Cletho’s script)  
- **Step metadata** (where in the decision cycle the conversation is)  
- **Distilled session context** (summaries or embeddings of the current and prior sessions)

This approach avoids feeding an ever-growing transcript into the retriever. Instead, it uses structured memory (summaries, embeddings, artifacts) to keep queries concise and contextually rich.

---

## Interaction & Memory Boundaries

The architecture distinguishes between three key boundaries:

1. **Decision Cycle (DC)**  
   - Full journey from *“I want to make a decision”* to *“I’m done with this decision.”*  
   - Persistent container for all inputs, artifacts, and outputs.  
   - Each DC has a unique ID (e.g., `dc_2025-08_portugal`).  

2. **Decision Cycle Step (DC-Step)**  
   - One of ~11 logical phases of the decision process (Introduction, Framing, Options, Payoffs, Probabilities, Utilities, Heuristics, Interpretation, What Could Go Wrong, Conclusion).  
   - Each step is script-driven and may carry explicit RAG hooks (e.g., `rag_trigger: true`, `rag_purpose: example`).  
   - Each step maintains summaries and structured outputs (e.g., *“User identified three options and noted concern about costs.”*).  

3. **Session (temporal)**  
   - One login-to-logout interaction with Cletho.  
   - Sessions may cross step boundaries, and multiple sessions can belong to a single DC.  
   - Each session ends with an explicit user-off signal (e.g., *“I’m done for now”*).  
   - Sessions produce summaries and embeddings for future retrieval.  
   - For MVP, retrieval will use the **most recent session summary** in its entirety; longer-term, this may evolve to **chunked, retrievable summaries**.

These three boundaries give the RAG system clear scaffolding for what to store, when to summarize, and how to recall information later.

---

## Corpus Scope

Cletho’s RAG corpus is **internal-only.** At MVP:

- No live external API calls  
- No web search integrations  
- No arbitrary user-upload ingestion  

Instead, the curated corpus will include:

- **Conceptual definitions** (e.g., Expected Utility, Ambiguity Aversion)  
- **Bias exemplars** (e.g., Anchoring, Framing, Availability)  
- **Worked examples** (e.g., Umbrella vs Sunglasses, Startup Valuation)  
- **Decision matrix theory chunks**  
- **Philosophical references** (e.g., Pascal’s Wager, Buridan’s Ass)  
- **Templates and heuristics checklists**

**Corpus structure:** Use a **hybrid model**. Author knowledge in Markdown (under version control), ingest into **Supabase** as chunked, embedded entries with metadata for retrieval.  

The separation between **knowledge corpus** and **user data** (decisions, sessions, matrices, logs) is a strict design constraint, both for privacy and for maintainability.

---

## Retrieval Modes

The RAG system must support **three retrieval modes**:

1. **Keyword search**  
2. **Semantic search** (priority emphasis)  
3. **Metadata filtering** (by step, type, tag, etc.)

The design is hybrid — meaning retrieval queries can combine all three.

---

## Zero-/Few-Shot LLM Classifier (MVP Spec)

**Purpose.** Label each turn and decide whether to trigger RAG, with what purpose, and what to use as the query source.

**Labels & Fields**
- `origin`: `"user" | "script"`
- `turn_type`: `"question" | "answer" | "statement"`
- `rag_trigger`: boolean
- `rag_purpose`: array of enums from  
  `["definition","example","scaffold","bias_check","clarification","citation"]`
- `query_focus`: `"current_turn" | "step_prompt" | "session_summary" | "mixed"`
- `confidence`: 0.0–1.0
- `notes`: short rationale (≤30 words)

**Trigger Policy (MVP)**
- `origin="script"` AND step carries a RAG hook ⟶ `rag_trigger=true` with purpose from the hook.  
- `origin="user"` AND `turn_type="question"` ⟶ `rag_trigger=true`, purpose inferred (`definition|example|clarification|citation`).  
- `origin="user"` AND `turn_type in {"answer","statement"}` ⟶ trigger only if:  
  (a) step requires missing info the KB can scaffold,  
  (b) bias is explicitly mentioned (→ `bias_check`), or  
  (c) user requests help implicitly (“I don’t understand…”, “hard to compare…”).

**Query Source Rule**
- Default `query_focus="mixed"`: current turn + step metadata + most-recent session summary.  
- If `origin="script"` and hook specifies, honor it (e.g., `step_prompt`).  
- If question asks for a definition/exemplar, bias toward `current_turn`.

**Output Contract (JSON only)**

```json
{
  "origin": "user",
  "turn_type": "question",
  "rag_trigger": true,
  "rag_purpose": ["definition"],
  "query_focus": "current_turn",
  "confidence": 0.86,
  "notes": "User asked for a definition; step=Framing."
}
```

## Data & Storage

- **Backend:** Supabase (Postgres)  

- **Entities (suggested):**  
  - `decisions` (DC-level records)  
  - `dc_steps` (step definitions and logs)  
  - `sessions` (temporal records)  
  - `session_summaries` (narrative + embeddings)  
  - `matrix_artifacts` (structured decision data)  
  - `kb_documents` (knowledge base sources)  
  - `kb_chunks` (retrieval units, with embeddings + metadata)  
  - `retrieval_logs` (queries, hits, usage context)  

- **Separation of domains:**  
  - **User data** (decisions, sessions, matrices) is stored and accessed separately from the **knowledge corpus**.  
  - This ensures privacy, traceability, and maintainability.  

Jeff’s two requirements are locked in here: **Supabase as the database backend** and **clear data boundary** between user data and knowledge corpus.

---

## MVP Definition (Minimum Viable RAG)

For the seven-week build, **minimum viable RAG** means:

1. A curated internal corpus, chunked with embeddings + metadata.  
2. Dual-trigger retrieval (user + script) working in at least two DC steps.  
3. Classifier → query-builder → retriever → cite-aware output pipeline.  
4. Session/DC summaries created and retrievable for future turns.  
5. Supabase schema enforcing domain separation (user data vs KB).  

**Evaluation:** For MVP, log all retrievals and manually review weekly. Define success as: *≥1 relevant chunk in top-3 results for ≥80% of representative queries.* Add **step-success tracking** later when end-to-end flows are exercised.

---

## Closing Note

The essence of Cletho’s RAG is not just answering questions, but **supporting the process** of building, interpreting, and reflecting on decision matrices. The retrieval system exists to bring in the right knowledge at the right time — sometimes because the user asks for it, and sometimes because Cletho knows the script calls for it.  

Keep that duality in mind as you design, and remember: modularity and separation of concerns (**user data vs knowledge base, short-term vs long-term memory, retrieval vs reasoning**) are what will keep this system robust as it grows.


