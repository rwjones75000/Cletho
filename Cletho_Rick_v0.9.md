# Cletho Requirements — Rick Pass (v0.9)
*Elicited on: 2025-06-21 | Analyst: Cassia | Stakeholder: Rick Jones*

---

## 1. Stakeholder Goals

| ID   | Goal Statement |
|------|----------------|
| G-01 | Enable users to make well-structured decisions under conditions of risk or uncertainty. |
| G-02 | Surface and examine the user's assumptions and possible cognitive biases during decision-making. |
| G-03 | Foster user understanding and confidence through guided inquiry rather than prescriptive advice. |
| G-04 | Encourage users to gain insight into, and actively mitigate, cognitive biases that may affect their decisions. |

---

## 2. Functional Requirements

### Decision Modeling (Risk and Uncertainty)

| ID   | Statement |
|------|-----------|
| FR-01 to FR-06 | Define the matrix-building process (steps 1–6), including fallback to uncertainty heuristics and optional utility functions. |
| FR-40 to FR-44 | Implement the six-step construction of a decision matrix under risk. |
| FR-45 to FR-47 | Support heuristics for uncertainty decisions (maximin, maximax, Laplace, Hurwicz, minimax regret). |
| FR-48 | Allow switching from risk to uncertainty mode if probabilities cannot be assigned. |

### Dialog and Interaction

| ID   | Statement |
|------|-----------|
| FR-19 to FR-26 | Support stepwise progression, flexible navigation, tone customization, recaps, and partial transcripts. |
| FR-31 to FR-34 | Generate transcripts, summaries, and structured decision cycle logs. |

### User Roles

| ID   | Statement |
|------|-----------|
| FR-35 to FR-39 | Define individual and institutional users; support shared sessions and future role tagging. |

### Data Handling and Privacy

| ID   | Statement |
|------|-----------|
| FR-11 to FR-18 | Authentication, GDPR compliance, server-side storage, user rights to delete, and long-term retention flags. |

---

## 3. Non-Functional Requirements

| ID   | Statement |
|------|-----------|
| NFR-01 to NFR-17 | Cover Socratic style, no advice, ethical boundaries, usability tiers, error handling, transparency, and interpretability. |

---

## 4. Deferred Features (Roadmap)

| ID     | Description |
|--------|-------------|
| FUT-01 | Ergodic model support |
| FUT-02 | Expandable bias detection library |
| FUT-03 | Custom matrix editor |
| FUT-04 | Role assignment in team sessions |
| FUT-05 | Long-term legal retention |
| FUT-06 | Offline mode |
| FUT-07 | Modal evolution: text → speech → 2D/3D avatars |

---

## 5. Open Questions

| ID      | Topic |
|---------|-------|
| OPEN-01 | Institutional audit permissions and access control |

---

*End of v0.9 Rick Requirements Snapshot*