## Preliminary Project Description: *Predictive Coding as an Algorithmic Implementation of RSA for Vagueness, with an Extension to Nouns*

**Motivation & Goal.**
The Rational Speech Act (RSA) framework (Lassiter & Goodman, 2015 ([Stanford][1])) models vagueness for gradable adjectives (e.g., *tall*) by treating the adjective’s threshold as a free variable inferred jointly with the world state in a speaker–listener game. This model accounts for context sensitivity, borderline uncertainty, and sorites-like judgments without special semantic machinery. What RSA leaves open is the process by which listeners compute these posteriors online and how precision (confidence) is set. This project proposes a predictive-coding (PC) implementation of RSA: RSA provides the computational target (the joint posterior over answers and thresholds), and PC supplies the algorithmic procedure (precision-weighted prediction-error minimization) to reach it. I will replicate core RSA results for adjectives and extend the same mechanism to nouns, comparing two noun templates: thresholded (e.g., *weapon*, *child*) and prototype/region categories (e.g., *cup/bowl*, *bird*).

**Core idea.**
Lassiter & Goodman's "Adjectival vagueness in a Bayesian model of interpretation" (2015) proposes a formal model of how the free threshold in adjectives are determined in-context, which they named the Rational Speech Act (RSA). This model adopts a three-step recursive bayesian inference approach: the pragmatic listener L1 infers world state (A) from the utterance (u) of the speaker S1, who infers the utterance from a supposed literal listener(L0)'s world state, who infers the world state given the literal meaning of u is true. The function performed by each agent is as follows: <br>
$$
P_{L_0}(A \mid u, V) \;=\; P_{L_0}\!\big(A \mid \llbracket u \rrbracket_V = 1\big)
$$
<br>
$$
P_{S_1}(u \mid A, V) \;\propto\; 
\exp\!\Big(\alpha \big[\ln P_{L_0}(A \mid u, V) - C(u)\big]\Big)
$$
<br>
$$
P_{L_1}(A, V \mid u) \;\propto\; P_{S_1}(u \mid A, V)\,P_{L_1}(A)\,P_{L_1}(V)
$$
<br>
(!need to figure out LaTex embedding)
**Predictive-coding implementation.**
PC is an approximate Bayesian inference scheme where top-down predictions and bottom-up, precision-weighted errors are iteratively updated. In this project, observing an utterance `u` drives error units on the “utterance” node (a categorical/softmax likelihood mirroring `S1`’s choice model), and updates flow to the latent variables for `A` and `V` until they settle near `P(A, V | u)`. Precision (inverse variance) acts as a control knob predicting trial-wise confidence and speed (e.g., sharper priors or stronger cues → faster, more confident convergence). This connects RSA’s interpretive posteriors to behavioral and neurocognitive signatures argued to reflect predictive processing.

**Work package 1 — Replicate RSA results with PC.**

1. **Model fit:** Reproduce key simulations under PC inference (e.g., “Al is tall”) using Normal priors on heights and a uniform prior on `θ`, with alternative set `ALT = {positive adjective, antonym, ∅}`, cost proportional to length, and softmax temperature `α`. Evaluate whether the PC dynamics produce the same marginals over `A` and `θ` reported by L&G (posteriors concentrated around “significantly greater than average” yet still vague).
2. **Context sensitivity:** Shift the prior mean/variance (comparison class) and show corresponding shifts in `θ` and truth judgments, as in L&G’s Figure 7.
3. **Sorites:** Compute the probabilities of inductive premises under two readings (material-conditional and Adams’ Thesis `P(B | A)`), and under L&G’s “free-variable in the conditional” interpretation that conditions on a cooperative assertion. The target pattern is high-probability premises with a low-probability absurd conclusion.

**Work package 2 — Extend to nouns.**
I will reuse the free-parameter model at the semantic interface and the same RSA-PC inference loop. Two noun types:

* **Thresholded nouns (soritical):** Introduce a latent boundary `θ_N` over a salient scalar (e.g., harmfulness for *weapon*, age for *child*). Truth = `μ_N(x) > θ_N`. Infer `(A, θ_N)` under RSA-PC from uses like “That is a weapon,” predicting graded borderline membership and sorites-like tolerance. (Direct analogue of the adjective case.)
* **Prototype/region nouns (polythetic):** Represent categories as regions in a conceptual space with latent prototype `μ`, dimension weights `w`, and tolerance `τ`. Truth ≈ `sim(x, μ; w) > τ`. Treat `V = {μ, w, τ}` as free variables inferred in the RSA-PC loop; predict context-sensitive category boundaries and gradedness when priors over features or QUD vary. (Complements L&G’s note that non-scalar vagueness likely requires such extra structure.)

**Methodological details (shared across WP1–2).**

* **Generative assumptions.** QUD-relative utility; cost ~ utterance length; ALT sets tailored to each domain (e.g., `{cup, bowl, ∅}`). Priors over degrees/features set from published norms or simple Gaussians/Beta distributions; uniform priors on free semantic variables unless data suggest otherwise.
* **Recognition dynamics.** PC message passing with precision scheduling; softmax likelihood for discrete `u`. Convergence diagnostics (free-energy decrease), and ablations varying `α`, costs, and ALT to test robustness and identifiability.
* **Evaluation.** (i) **Judgment-level:** Posterior predictive fits to graded truth/acceptability and borderline membership (Eq. 32-style integrals). (ii) **Process-level (exploratory):** Predict how manipulations that tighten priors (e.g., explicit comparison classes, intensifiers) should speed convergence and increase confidence, aligning with precision-based interpretations of reading time and N400 effects.

**Expected contributions.**

1. A unifying account that ties RSA’s explanatory successes in vagueness to an explicit, neurally-plausible inference mechanism (PC).
2. A portable implementation (adjectives → nouns) showing that pragmatic inference over free semantic parameters generalizes beyond degrees.
3. Concrete, testable process-level predictions (confidence, speed) that are absent in a purely computational-level RSA story.

**Feasibility & plan.**

* **Weeks 1–2:** Reproduce baseline RSA simulations (static inference) and align notation/datasets.
* **Weeks 3–5:** Implement PC inference for the RSA generative model; validate on adjective case.
* **Weeks 6–8:** Systematic parameter sweeps (priors, ALT, costs, `α`); replicate context and sorites results.
* **Weeks 9–10:** Extend to nouns (thresholded, then prototype/region); compare models.
* **Weeks 11–12:** Write-up; prepare code appendix and figures matching L&G’s diagnostics.

**Risks & mitigations.**

* *Discrete utterances in PC:* use a categorical/softmax node (or Gumbel-softmax for gradients).
* *Identifiability of `θ` vs prior scale:* anchor priors from norms; report sensitivity; include ALT/cost ablations.
* *Noun model complexity:* start with scalar/thresholded nouns; prototype/region as stretch target.

[1]:https://cocolab.stanford.edu/papers/LassiterGoodman2015-Synthese.pdf
