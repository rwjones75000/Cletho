# Decision Theory Terminology  

<!-- Cletho Knowledge Base Document | Seed Corpus | MVP-1.0 -->

---

title: "Decision Theory Terminology"   
version: "MVP-1.0"   
type: "definition"   
tags: ["decision_theory", "terminology"]   
step_tags: ["rational-choice", "bounded-rationality", “heuristics”, "preferences", "utility", “value”, "risk", "uncertainty", "behavioral-bias", “cognitive-bias”, "normative", "descriptive", "prescriptive", "game-theory", "optimization", "probability", "statistics", “base-rate”, “reference-class”, expected-value”, “payoffs”, “expected-utility”, risk-preference”, “ambiguity”]   
created_at: 2025-09-16   
updated_at: 2025-09-16   
provenance: "Curated internal corpus (Clear Thought Labs)"   
notes: "Part of MVP seed corpus. Complements Decision Matrix Terminology by covering broader theoretical foundations of decision science."   

---

## Decision Theory
<!-- meta: { 
  "content_type": "definition", 
  "step_tags": ["rational-choice", "uncertainty"], 
  "aliases": ["theory-of-decision", "choice-theory"] 
} -->

### Definition
Decision theory is the study of how choices are or should be made under conditions of uncertainty, risk, or conflicting objectives.  

### Explanation
It encompasses three perspectives:  
- **Normative** — how rational decision makers *should* decide if they aim to maximize coherence and consistency (e.g., expected utility theory).  
- **Descriptive** — how people *actually* make decisions, including biases, heuristics, and psychological influences (e.g., prospect theory).  
- **Prescriptive** — methods and tools that help people make better decisions, bridging the gap between the normative ideal and descriptive reality.  

Decision theory underpins fields such as economics, operations research, cognitive psychology, artificial intelligence, and game theory. It provides the formal scaffolding for decision matrices, expected value, and utility theory.

### Example
A public health agency deciding whether to fund vaccination programs draws on decision theory: normative models calculate expected benefits, descriptive research anticipates public hesitancy, and prescriptive tools (like structured decision aids) guide practical policy choices.

---

## Rational Choice
<!-- meta: { 
  "content_type": "definition", 
  "step_tags": ["rational-choice", "preferences", "utility"], 
  "aliases": ["rational-decision-making", "rational-agent-model"] 
} -->

### Definition
Rational choice is a model of decision-making in which agents select the option that maximizes their expected utility given consistent preferences and available information.  

### Explanation
The rational choice model assumes:  
1. **Complete preferences** — every pair of alternatives can be compared.  
2. **Transitive preferences** — if A is better than B and B is better than C, then A is better than C.  
3. **Utility maximization** — choices are made to maximize satisfaction according to a utility function.  
4. **Consistent probability use** — uncertainty is represented and combined according to probability theory.  

Though influential, rational choice is often criticized as unrealistic when applied to human behavior, since real people deviate systematically from its assumptions.

### Example
In classical economics, a consumer choosing between apples and oranges is modeled as weighing costs and benefits and selecting whichever maximizes utility, subject to budget constraints.

---

## Bounded Rationality
<!-- meta: { 
  "content_type": "definition", 
  "step_tags": ["bounded-rationality", "heuristics"], 
  "aliases": ["satisficing", "limited-rationality"] 
} -->

### Definition
Bounded rationality is the idea that decision-makers operate under constraints of limited information, limited time, and limited cognitive capacity, leading them to use simplified strategies instead of full optimization.  

### Explanation
Herbert Simon introduced the concept to explain why real-world decision-makers rarely achieve perfect rationality. Instead, they:  
- Use **heuristics** (rules of thumb) to simplify complexity.  
- Seek **satisficing** solutions — good enough, rather than optimal.  
- Focus on **search and stopping rules** that balance costs of further analysis against potential gains.  

Bounded rationality reframes decision-making as adaptive within constraints, making it more realistic and applicable to human behavior and organizational processes.

### Example
A hiring manager who needs to fill a role quickly may stop interviewing after finding the first candidate who meets all basic qualifications, rather than continuing until the absolute best candidate is found.

---

## Utility
<!-- meta: { 
  "content_type": "definition", 
  "step_tags": ["utility", "preferences", "values"], 
  "aliases": ["subjective-value", "preference-scale"] 
} -->

### Definition
Utility is a numerical representation of how much a decision-maker values an outcome, reflecting preferences rather than objective measures like money alone.  

### Explanation
Utility theory provides a way to model subjective preferences:  
- **Ordinal utility** ranks outcomes without specifying intensity (e.g., A is better than B is better than C).  
- **Cardinal utility** assigns numbers that preserve both ranking and relative strength (e.g., utility of A = 10, utility of B = 6).  
- **Von Neumann–Morgenstern utility** formalizes preferences under uncertainty, enabling expected utility calculations.  

Utility is central to rational choice models, though behavioral research shows that real-world preferences often violate utility assumptions.

### Example
For a relatively poor person, $100 may have a utility of 50 (life-changing if resources are scarce), while for a billionaire it may have utility close to zero.

---

## Risk vs. Uncertainty
<!-- meta: { 
  "content_type": "comparison", 
  "step_tags": ["risk", "uncertainty"], 
  "aliases": ["risk-uncertainty-distinction", "knightian-uncertainty"] 
} -->

### Definition
Risk and uncertainty both involve unknown outcomes, but risk refers to situations where probabilities are known or knowable, while uncertainty refers to situations where probabilities are unknown or unknowable.  

### Explanation
- **Risk** — can be quantified and incorporated into models (e.g., a fair coin toss).  
- **Uncertainty** — cannot be reduced to probabilities (e.g., whether a new technology will disrupt an industry in 10 years).  

This distinction, emphasized by economist Frank Knight, is critical because many real-world decisions involve uncertainty rather than calculable risk. Decision frameworks must adapt accordingly (e.g., scenario planning, heuristics, robust decision-making).

### Example
Investing in government bonds is a decision under risk (probabilities of default are well-estimated). Investing in a brand-new cryptocurrency is a decision under uncertainty (no reliable probabilities exist).

---

## Behavioral Bias
<!-- meta: { 
  "content_type": "definition", 
  "step_tags": ["behavioral-bias", “cognitive-bias”, "descriptive"], 
  "aliases": ["cognitive-bias", "systematic-error"] 
} -->

### Definition
Behavioral biases are systematic patterns of deviation from rational choice, often arising from heuristics, emotions, or social influences.  

### Explanation
Biases are not random mistakes but predictable tendencies. Examples include:  
- **Loss aversion** — losses loom larger than equivalent gains.  
- **Overconfidence** — overestimating knowledge or control.  
- **Anchoring** — relying too heavily on initial information.  
- **Availability bias** — judging probability based on ease of recall.  

Understanding biases is central to descriptive decision theory and behavioral economics, and prescriptive methods often aim to mitigate their effects.

### Example
In retirement planning, many people under-save because they anchor on low default contribution rates set by employers, even when higher savings would be optimal.

---

## Normative vs. Descriptive vs. Prescriptive
<!-- meta: { 
  "content_type": "comparison", 
  "step_tags": ["normative", "descriptive", "prescriptive"], 
  "aliases": ["decision-theory-approaches"] 
} -->

### Definition
Decision theory can be divided into three approaches:  
- **Normative** — how ideal rational agents *should* decide.  
- **Descriptive** — how real humans *actually* decide.  
- **Prescriptive** — how to help people

## Probability
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["probability", "uncertainty", "likelihood"],
  "aliases": ["chance", "odds", "likelihood"]
} -->

### Definition
Probability is a numerical measure (from 0 to 1) of how likely an event or state of nature is to occur, with 0 meaning impossible and 1 meaning certain.

### Explanation
Probabilities make uncertainty computable. When the relevant states of nature are mutually exclusive and collectively exhaustive, their probabilities sum to 1. Probabilities can be assigned from theory (e.g., symmetry), data (frequencies), or judgment (expert belief). Once assigned, they support downstream calculations like **expected value** and **expected utility**, enabling consistent comparison of alternatives.

### Example
A weather service estimates a 30% (0.3) probability of rain tomorrow and a 70% (0.7) probability of no rain. Planning a picnic becomes a decision under uncertainty informed by these probabilities.

---

## Probability Types
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["probability-types", "probability", "statistics"],
  "aliases": ["a-priori", "empirical", "subjective", "Bayesian"]
} -->

### Definition
Probability types are distinct ways of justifying or deriving probabilities: **a priori**, **empirical**, and **subjective** (often updated via **Bayesian** reasoning).

### Explanation
- **A priori (theoretical)** — Derived from known structure or symmetry, without data.  
  *Use when* the mechanism is well-defined (e.g., fair dice).  
- **Empirical (frequentist)** — Estimated from observed frequencies in data drawn from a reference class.  
  *Use when* you have adequate, relevant historical data.  
- **Subjective (judgmental)** — Elicited from expert belief or informed intuition when data are sparse or not directly applicable.  
  *Use when* facing novel or poorly measured phenomena.  
- **Bayesian updating (method, not a distinct category)** — Start with a prior (often subjective or based on base rates), incorporate new evidence via likelihoods, and compute a posterior probability.

### Example
Launching a new product:  
- A priori: none (market behavior lacks symmetry).  
- Empirical: estimate adoption rates using data from similar products (reference class).  
- Subjective: adjust for unique features (brand strength, timing).  
- Bayesian: after initial sales, update the prior success probability with observed early uptake.

---

## Base Rate
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["base-rate", "reference-class", "statistics"],
  "aliases": ["prior-probability", "reference-rate"]
} -->

### Definition
A base rate is the background prevalence or frequency of an event within a defined **reference class**, used as prior information before considering case-specific details.

### Explanation
Base rates anchor probability judgments in population-level data and help avoid the **base rate fallacy**—overweighting vivid case details while ignoring broad frequencies. In decision analysis, base rates frequently inform priors for Bayesian updates or the probabilities assigned to states of nature in a matrix.

### Example
If historically 20% of comparable software startups reach profitability within three years, that 20% is the base rate. An investor should weigh this fact alongside the specific team, product, and market evidence.

---

## Expected Value (EV)
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["expected-value", "probability", "payoffs"],
  "aliases": ["EV", "mean-payoff"]
} -->

### Definition
Expected value (EV) is the probability-weighted average of possible **payoffs** for a decision:  
\[
\mathrm{EV} = \sum_i p_i \cdot x_i
\]
where \(p_i\) are probabilities and \(x_i\) are payoffs.

### Explanation
EV represents the long-run average outcome if the decision were repeated under the same probabilities. It presumes payoffs are on a common, linear scale (e.g., money) and does **not** incorporate risk preferences. EV is often computed in the far-right column of a decision matrix to compare courses of action.

### Example
A supplier can accept a rush order with two outcomes:  
- On-time bonus: +\$40k with probability 0.6  
- Late penalty: −\$10k with probability 0.4  
EV \(= 0.6 \cdot 40{,}000 + 0.4 \cdot (-10{,}000) = 24{,}000 - 4{,}000 = \$20{,}000\).  
On EV grounds, accepting the order is favorable.

---

## Expected Utility (EU)
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["expected-utility", "probability", "risk-preference"],
  "aliases": ["EU", "utility-expectation"]
} -->

### Definition
Expected utility is the probability-weighted average of **utilities** (subjective values of outcomes), not raw payoffs:  
\[
\mathrm{EU} = \sum_i p_i \cdot u(x_i)
\]
where \(u(\cdot)\) is the decision-maker’s utility function.

### Explanation
EU incorporates risk attitudes and diminishing sensitivity to gains/losses. With a **concave** utility function (risk aversion), the utility of an extra dollar is smaller when you already have many dollars; a **convex** function implies risk seeking; **linear** implies risk neutrality. EU is the normative standard for rational choice under risk because it matches how preferences over lotteries should behave if they are coherent.

### Example
Choose between:  
- A sure \$50  
- A 50–50 gamble for \$120 or \$0 (EV \$60)  
A risk-averse person with concave utility may prefer the sure \$50 because \(0.5 \cdot u(120) + 0.5 \cdot u(0) < u(50)\), even though the gamble’s EV is higher.

---

## Risk
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["risk", "probability"],
  "aliases": ["quantifiable-uncertainty"]
} -->

### Definition
Risk is uncertainty with **known or estimable probabilities** over outcomes.

### Explanation
Under risk, you can assign probabilities to states of nature using theory, data, or elicited beliefs. This enables EV/EU calculations, variance/Value-at-Risk metrics, and hedging strategies. Many financial, reliability, and operations problems are modeled as decisions under risk.

### Example
A portfolio manager knows (from historical volatility and models) the distribution of monthly returns for a balanced fund. Allocation decisions (stocks vs. bonds) are made by weighing expected return against risk measures like standard deviation.

---

## Uncertainty
<!-- meta: {
  "content_type": "definition",
  "step_tags": ["uncertainty", "ambiguity"],
  "aliases": ["Knightian-uncertainty", "deep-uncertainty", "ambiguity"]
} -->

### Definition
Uncertainty (often “Knightian uncertainty”) is the condition where **reliable probabilities are unknown or unknowable**.

### Explanation
When data are scarce, mechanisms are poorly understood, or the future is structurally novel, probability assignments are fragile. In such settings, robust or adaptive approaches (scenario planning, minimax regret, info-gathering experiments, option value, and staged commitments) often dominate pure EV/EU analysis.

### Example
A city considering a first-of-its-kind climate adaptation project cannot credibly assign probabilities to long-horizon sea-level scenarios. It may choose a robust design that performs acceptably across a wide range of possibilities, rather than one that is optimal for a single forecast.

---

## Risk vs. Uncertainty (Comparison)
<!-- meta: {
  "content_type": "comparison",
  "step_tags": ["risk", "uncertainty", "probability"],
  "aliases": ["risk-uncertainty-distinction"]
} -->

### Definition
Both involve unknown outcomes; **risk** has **known/estimable** probabilities, **uncertainty** lacks credible probabilities.

### Explanation
- **Modeling**: Risk → probabilistic models; Uncertainty → scenarios/robustness.  
- **Evaluation**: Risk → EV/EU and risk metrics; Uncertainty → regret, dominance, flexibility, information value.  
- **Action**: Risk → optimize/hedge; Uncertainty → stage decisions, keep options open, invest in learning.

### Example
Choosing car insurance (rich actuarial data) is a decision under **risk**. Choosing a business model around a just-released, unproven technology is a decision under **uncertainty**.

---

