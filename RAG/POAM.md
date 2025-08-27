# Cletho MVP RAG – High-Level Project Plan

Target: **Working MVP by mid-October 2025 (7 weeks)**

| **Week** | **Focus** | **Milestones / Deliverables** |
|----------|-----------|--------------------------------|
| Week 1 <br> (late Aug – early Sept) | **Foundations** | - Supabase account created <br> - `pgvector` enabled <br> - Separate schemas (`kb.*`, `app.*`) created <br> - Draft schema for documents, chunks, decisions, sessions, summaries |
| Weeks 2–3 <br> (early–mid Sept) | **Corpus + Retrieval Core** | - Seed corpus loaded (definitions, bias exemplars, worked examples) <br> - Ingestion script for Markdown → chunks → embeddings <br> - Basic retrieval tested (semantic, keyword, metadata separately) <br> - Prototype hybrid retrieval query (combine scores) |
| Weeks 4–5 <br> (mid–late Sept) | **Orchestration Layer** | - Zero-/few-shot classifier implemented (JSON labels) <br> - Query Builder built (turn + step metadata + session summary) <br> - RAG trigger policies wired for both user + script flows <br> - Retriever + LLM wrapper loop working <br> - Retrieval logs captured in Supabase |
| Weeks 6–7 <br> (late Sept – mid Oct) | **Integration + Proof** | - At least 2 Decision Cycle Steps encoded with RAG hooks (e.g., Framing, Payoffs) <br> - Demonstration of dual flows: <br> &nbsp;&nbsp;• User-originated input → retrieval → response <br> &nbsp;&nbsp;• Script-originated step → retrieval → question posed <br> - Session summaries stored with embeddings <br> - Weekly evaluation runs (top-3 relevance ≥ 80%) <br> - Demo notebook / lightweight front-end for end-to-end test |

---

## ✅ Mid-October Deliverable

- Supabase as unified backend (KB + user data).  
- Retrieval working across curated seed corpus.  
- Both **user-originated** and **system-originated** flows functional in ≥2 steps.  
- Hybrid retrieval (keyword + semantic + metadata).  
- Logs and session summaries stored for review.  
