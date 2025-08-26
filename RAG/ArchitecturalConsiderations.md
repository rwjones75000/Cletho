# Architectural Considerations: Cletho’s Minimum Viable RAG System

This document captures the principal architectural features of the RAG system for Cletho, as they stood at the end of August 2025. It is written so that if all prior documentation is lost, a future reader (human or AI) will still understand the reasoning and design intent.

---

## Purpose

Cletho is a decision assistant designed to help users make complex decisions through a structured, multi-step dialogue. That dialog consists primarily of Cletho asking the user questions in order to (1) build out a decision matrix, and (2) identify any cognitive biases that may be affecting the user’s reasoning.

To support this, Cletho requires a ** retrieval-augmented generation (RAG) system**.   

Unlike most RAG systems, which are designed to answer **user-prompted questions**, Cletho’s variant must primarily support **system-initiated prompts** that emerge from scripted steps in a decision-making and cognitive bias identifying framework.

---

## Retrieval Triggers

Cletho’s RAG is **dual-triggered**:

1. **Script-originated events**  
   Retrieval will be triggered from Cletho’s internal scripts, for example:  
   - When a step calls for a **definition or explanation**  
   - When a worked **example** or template is useful  
   - When Cletho needs to surface **heuristics or bias checks**


2. **User-originated input**  
   Retrieval may also be initiated by any form of user input, not just explicit questions. Examples:  
   - A direct **question**: *“What’s expected utility?”*  
   - An **answer** to Cletho’s question: *“I think anchoring is affecting me here.”*  
   - A **statement or reflection**: *“This payoff seems hard to compare.”*

This design means the retrieval system is not simply reactive — it is woven into the procedural flow of Cletho’s dialogue.

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

These three boundaries give the RAG system clear scaffolding for what to store, when to summarize, and how to recall information later.

---

## Corpus Scope

Cletho’s RAG corpus is **internal-only**. At MVP:

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

This corpus is the knowledge base Cletho will rely on. The separation from **user data** (e.g., decision matrices, preferences, logs) is strict and deliberate.

---

## Retrieval Modes

The RAG system must support **three retrieval modes**:

1. **Keyword search**  
2. **Semantic search** (priority emphasis)  
3. **Metadata filtering** (by step, type, tag, etc.)

The design is hybrid — meaning retrieval queries can combine all three.

---

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

---

## MVP Definition (Minimum Viable RAG)

For the seven-week build, **minimum viable RAG** means:

1. A curated internal corpus, chunked with embeddings + metadata.  
2. Dual-trigger retrieval (user + script) working in at least two DC steps.  
3. Classifier → query-builder → retriever → cite-aware output pipeline.  
4. Session/DC summaries created and retrievable for future turns.  
5. Supabase schema enforcing domain separation (user data vs KB).  

---

## Closing Note

The essence of Cletho’s RAG is not just answering questions, but **supporting the process** of building, interpreting, and reflecting on decision matrices. The retrieval system exists to bring in the right knowledge at the right time — sometimes because the user asks for it, and sometimes because Cletho knows the script calls for it.  

Keep that duality in mind as you design, and remember: modularity and separation of concerns (user data vs knowledge base, short-term vs long-term memory, retrieval vs reasoning) are what will keep this system robust as it grows.

