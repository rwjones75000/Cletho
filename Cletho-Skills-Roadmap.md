# ✅ Cletho Developer Roadmap: Skill Mastery Checklist

This checklist covers the three core technical skill areas needed to build Cletho's components, progressing from foundational tasks to system-level integration.

---

## Skill Track 1: Python Application Development

- [ ] Write modular Python functions for input → output transforms
- [ ] Define and use Python classes (e.g., `DecisionMatrix`, `DialogueState`)
- [ ] Read and write JSON for internal communication between components
- [ ] Use virtual environments (`venv`, `pip`) to manage dependencies
- [ ] Write unit tests with `pytest` to cover edge cases
- [ ] Create and expose a REST API using Flask or FastAPI
- [ ] Implement structured logging and exception handling
- [ ] Use decorators or higher-order functions for traceability and control
- [ ] Orchestrate multi-step workflows across Cletho components
- [ ] Deploy a working API endpoint for a Cletho module (e.g., Question Generator)

---

## Skill Track 2: LLM API Integration & Prompt Control

- [ ] Make a basic call to OpenAI's `chat.completions.create` endpoint
- [ ] Use system and user roles effectively in prompt structure
- [ ] Write dynamic prompt templates using `.format()` or Jinja
- [ ] Include few-shot examples to condition Cletho's voice and behavior
- [ ] Wrap LLM calls into reusable Python functions
- [ ] Log all prompts and completions for analysis and debugging
- [ ] Experiment with model parameters (temperature, max tokens, stop sequences)
- [ ] Build a prompt scaffolding system for Cletho’s 6-step decision process
- [ ] Create prompt chains using intent classification + dynamic templates
- [ ] Implement fallbacks when the LLM produces out-of-bounds responses

---

## 📚 Skill Track 3: RAG and Knowledge Retrieval

- [ ] Chunk BK/TK/EK files into ~300–500 token segments
- [ ] Use `text-embedding-3-small` to embed text chunks
- [ ] Store embeddings with metadata using FAISS or Chroma
- [ ] Embed a user question and retrieve top-k chunks by similarity
- [ ] Index the entire knowledge library and test retrieval for coverage
- [ ] Build a Python wrapper for end-to-end RAG querying
- [ ] Insert retrieved knowledge into LLM prompts with citation tracking
- [ ] Implement filtering logic (e.g., by tag, file type, or source)
- [ ] Tune chunk size, overlap, and similarity thresholds for signal clarity
- [ ] Implement a fallback for low-confidence queries: “I don’t know.”

---

## Skill Track 4: Persistent Memory and State Management

This track focuses on the techniques Cletho will need to retain, retrieve, and revise session-specific information across multiple user interactions — without overstepping into personalization. The emphasis is on structured, inspectable memory that supports reasoning, transparency, and control.

- [ ] Understand and compare short-term memory (STM), long-term memory (LTM), and context window usage in LLMs  
- [ ] Represent memory explicitly using Python data structures (e.g., dictionaries, class instances, lists)  
- [ ] Build a `SessionMemory` class to track and update dialogue history, questions asked, and decisions in progress  
- [ ] Implement memory serialization (JSON, YAML, or pickle) to allow save/load of state  
- [ ] Log state transitions with timestamps and reasoning snapshots  
- [ ] Index memory entries for fast retrieval by topic, step, or user intent  
- [ ] Test replay of memory to resume interrupted sessions or review reasoning history  
- [ ] Enforce memory boundaries to prevent contamination (e.g., “session-only” vs “global” memory)  
- [ ] Integrate memory snapshots into prompts as structured input blocks  
- [ ] Simulate a complete session with multi-turn state tracking and regeneration

---  

## Optional Integration Milestones

- [ ] Integrate the RAG system with Cletho’s Dialogue Manager for Step 2 support
- [ ] Test prompt-only vs RAG-augmented response patterns
- [ ] Set up a project board to track development of Cletho modules
- [ ] Create GitHub issues or milestones mapped to this checklist

