# Cletho MVP – Project Charter

**Project Title:** Cletho MVP – Decision Partner Prototype  
**Project Sponsor:** Clear Thought Labs  
**Project Manager:** Rick  
**Proposed Launch Date:** Mid-January 2026  
**Version:** v0.1 Draft  
**Date:** 19 June 2025

---

## Purpose and Background

Cletho is a standalone, AI-powered decision partner designed to help individuals think more clearly and systematically through complex or uncertain decisions. Drawing on principles from decision theory, structured reasoning, and modular logic, Cletho supports users in mapping options, clarifying values, anticipating consequences, and comparing strategies.

The MVP aims to deliver a conversational prototype that demonstrates the value of AI-assisted decision structuring—without making decisions for the user. Instead, Cletho serves as a logic-based guide to help users navigate trade-offs and uncertainties in real-world contexts.

---

## Objectives

- Build a functional MVP that can:
  - Guide users through at least one full decision matrix
  - Apply multiple decision strategies (e.g., expected utility, maximin)
  - Incorporate at least three task-specific knowledge (TK) modules
  - Log user interactions, rationale, and selected strategies

- Deliver a technical foundation that:
  - Demonstrates modular reasoning workflows
  - Allows future expansion via new TK modules
  - Operates as a self-contained application

- Conduct internal evaluation and testing to inform future iterations

---

## Scope

**In Scope:**
- Core Cletho GPT instance (decision matrix engine)
- Initial set of TK modules (Pascal’s Wager, safety tradeoff, career decision)
- Conversational prompt architecture and task orchestration
- Simple user interface (chat or chat+visual)
- Logging and transparency framework

**Out of Scope:**
- Integration with external agents or virtual staff
- Long-term memory persistence across sessions
- Multi-user collaboration features
- Full onboarding or support portal

---

## Key Deliverables

| Deliverable            | Description                                     | Due          |
|------------------------|-------------------------------------------------|--------------|
| Requirements Document  | Clear functional and technical specs            | July 2025    |
| System Architecture    | Modular engine + reasoning strategies           | August 2025  |
| TK Modules             | Three use-case-specific templates               | September    |
| MVP Build              | Integrated GPT logic + interface                | November     |
| Evaluation Report      | Internal testing, benchmarks, feedback          | December     |
| Launch Bundle          | Deployed MVP + onboarding assets                | January 2026 |

---

## Timeline Summary

| Phase       | Duration      | Milestone            |
|-------------|---------------|----------------------|
| Planning    | June–July     | Requirements complete |
| Design      | July–August   | Architecture complete |
| Development | Sept–Nov      | Core system functional |
| Validation  | December      | Pilot tested          |
| Launch      | January       | MVP released          |

---

## Success Criteria

- Cletho guides users through a decision-making process without breaking flow
- Decision matrices are well-formed and interpretable by the system
- Justifications for outcomes are transparent and grounded in logic
- Users report increased clarity and confidence in reasoning
- Architecture supports future module expansion

---

## Risks and Assumptions

**Key Risks:**
- GPT outputs may diverge from formal logic
- TK module design may overfit examples
- Transparency could be compromised by LLM unpredictability
- MVP scope may expand beyond target

**Key Assumptions:**
- MVP will support single-user interaction only
- Long-term memory not required
- MVP built on OpenAI Custom GPT framework or equivalent
