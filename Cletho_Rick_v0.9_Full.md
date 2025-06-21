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

### Decision Matrix Construction (Risk Mode)

| ID     | Requirement Statement |
|--------|------------------------|
| FR-01 | Assist users in constructing a decision matrix under risk (expected value or expected utility) and uncertainty (heuristic-based). |
| FR-02 | Elicit and explicitly document all user-supplied assumptions. |
| FR-03 | Engage users in a dialog to help them recognize, learn about, and mitigate cognitive biases. |
| FR-04 | Support decision types including binary, multi-option, emotional, regret-driven, go/no-go, value-conflict, and ill-structured decisions. |
| FR-05 | Include a fixed set of well-established cognitive biases in the MVP. |
| FR-06 | Support institutional usage including internal-only, collaborative sessions, and model-based deployments. |
| FR-07 | Assume no prior user knowledge; begin with general and specific onboarding questions. |
| FR-08 | Guide users through a six-step decision matrix process: framing, actions, states, payoffs, probabilities, evaluation. |
| FR-09 | Allow users to pause/resume sessions and maintain state continuity across multi-day decision cycles. |
| FR-10 | Explain expected value vs. expected utility and assist in creating utility functions if desired. |
| FR-11 | Require user authentication before session start. |
| FR-12 | Store session data server-side. |
| FR-13 | Refrain from offering advice, suggestions, or opinions. |
| FR-14 | Inform users at the start of a decision cycle about data retention, deletion options, and default privacy policies. |
| FR-15 | Comply with GDPR, including data deletion on request. |
| FR-16 | Retain data throughout a decision cycle unless the user opts to delete it. |
| FR-17 | Offer data retention for post-cycle interactions. |
| FR-18 | Support legal retention policies for compliance purposes. |

### Interaction Model

| ID     | Requirement Statement |
|--------|------------------------|
| FR-19 | Guide users through step-by-step decision-making. |
| FR-20 | Allow recursive revisiting of earlier decision steps. |
| FR-21 | Allow users to select tone and dialog style at the start of a decision cycle. |
| FR-22 | Offer to update tone/style during the cycle. |
| FR-23 | Allow mid-session redirection or re-framing. |
| FR-24 | Notify users if the conversation drifts outside decision scope. |
| FR-25 | Offer session recaps when a user pauses. |
| FR-26 | Allow users to choose recap/summary formats. |
| FR-27 | Guide users through external decision matrix creation using general-purpose tools. |
| FR-28 | Offer summaries of biases encountered, with general definitions and mitigation strategies. |
| FR-29 | Provide full transcripts and segmented transcripts on demand. |
| FR-30 | Provide summaries of full or partial sessions. |
| FR-31 | Maintain structured decision cycle logs distinct from transcripts. |

### Risk & Uncertainty Modes

| ID     | Requirement Statement |
|--------|------------------------|
| FR-40 | Frame the decision problem. |
| FR-41 | Identify courses of action. |
| FR-42 | Identify states of nature. |
| FR-43 | Assign payoff values using quantification or 1–10 scale. |
| FR-44 | Assign probabilities with emphasis on base rates. |
| FR-45 | If probabilities fail, shift to heuristic-based method. |
| FR-46 | Re-explain EV vs. EU and offer utility modeling. |
| FR-47 | Provide guarded interpretation of results. |
| FR-48 | Support user-selected heuristics: maximin, maximax, Laplace, Hurwicz, minimax regret. |
| FR-49 | Explain each heuristic clearly before application. |
| FR-50 | Let users choose heuristics without system preference. |
| FR-51 | Enable switching from risk to uncertainty mode as needed. |

### Multi-User and Institutional Use

| ID     | Requirement Statement |
|--------|------------------------|
| FR-35 | Support individual and institutional user types. |
| FR-36 | Allow multi-user collaborative sessions. |
| FR-37 | Show unified dialogue to all participants. |
| FR-38 | Support turn-taking and annotation. |

---

## 3. Non-Functional Requirements

| ID     | Requirement Statement |
|--------|------------------------|
| NFR-01 | Do not assist in decisions involving illegal or morally ambiguous activities. |
| NFR-02 | Never fabricate functionality; acknowledge capability limits. |
| NFR-03 | Use Socratic and Rogerian dialog patterns. |
| NFR-04 | Avoid giving advice, recommendations, or opinions. |
| NFR-05 | Include onboarding and help modes. |
| NFR-06 | Assess user expertise and adapt dialog accordingly. |
| NFR-07 | Maintain humanlike pacing. |
| NFR-08 | Gracefully handle malformed or ambiguous inputs. |
| NFR-09 | Allow users to recover from input issues. |
| NFR-10 | Be fully transparent in reasoning and process. |
| NFR-11 | Let users inspect logic for decision matrix steps. |
| NFR-12 | Allow users to ask “why” Cletho posed a specific question. |

---

## 4. Roadmap / Deferred Capabilities

| ID     | Feature Description |
|--------|----------------------|
| FUT-01 | Ergodic decision models support. |
| FUT-02 | Expandable bias library. |
| FUT-03 | Native decision matrix editor. |
| FUT-04 | Role assignment in collaborative sessions. |
| FUT-05 | Long-term retention for legal purposes. |
| FUT-06 | Offline mode. |
| FUT-07 | Modal evolution from text → speech → 2D → 3D avatars. |

---

## 5. Open Items

| ID       | Topic |
|----------|-------|
| OPEN-01  | Institutional audit control and access rules |

---

*End of Cletho Requirements v0.9 — Rick Pass*