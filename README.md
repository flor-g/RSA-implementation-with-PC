## Project Description: Predictive Coding as an Algorithmic Implementation of RSA for Vagueness, with an Extension to Nouns

**Motivation & Goal.**
The Rational Speech Act (RSA) framework(Lassiter & Goodman 2015) explains vagueness for gradable adjectives (e.g., *tall*) by treating the adjective’s threshold as a free variable inferred jointly with the world state in a speaker–listener game. This yields context sensitivity, borderline cases, and sorites‑like judgments without special semantic machinery. What RSA leaves open is the *process* by which listeners compute these posteriors online and how precision (confidence) is set. This project proposes a predictive‑coding (PC) implementation of RSA: RSA provides the computational target (the joint posterior over answers and thresholds), and PC supplies the algorithmic procedure (precision‑weighted prediction‑error minimization) to reach it. I will replicate core RSA results for adjectives and extend the same mechanism to nouns, comparing two noun templates: thresholded (e.g., *weapon*, *child*) and prototype/region categories (e.g., *cup/bowl*, *bird*).  

**Core idea.**
In Lassiter & Goodman’s model, a literal listener (L_0) conditions on truth; a speaker (S_1) chooses utterances by a soft‑optimal trade‑off between informativity (relative to the Question Under Discussion, QUD) and cost; and a pragmatic listener (L_1) inverts the speaker to recover a joint posterior over the answer (A) (e.g., Al’s height) and semantic variables (V) (e.g., the threshold (\theta) for *tall*). Formally, (P_{S_1}(u\mid A,V)\propto \exp{\alpha(\text{informativity}*{L_0}-C(u))}) and (P*{L_1}(A,V\mid u)\propto P_{S_1}(u\mid A,V)P(A)P(V)). I adopt this as the **generative model** and implement the **recognition** dynamics with PC.  

**Predictive‑coding implementation.**
PC is an approximate Bayesian inference scheme where top‑down predictions and bottom‑up, precision‑weighted errors are iteratively updated. In this project, observing an utterance (u) drives error units on the “utterance” node (a categorical/softmax likelihood mirroring (S_1)’s choice model), and updates flow to the latent variables for (A) and (V) until they settle near (P(A,V\mid u)). Precision (inverse variance) acts as a control knob predicting trial‑wise confidence and speed (e.g., sharper priors or stronger cues → faster, more confident convergence). This connects RSA’s interpretive posteriors to behavioral and neurocognitive signatures argued to reflect predictive processing. 

**Work package 1 — Replicate RSA results with PC.**

1. **Model fit:** Reproduce key simulations under PC inference (e.g., “Al is tall”) using Normal priors on heights and a uniform prior on (\theta), with alternative set ALT = {positive adjective, antonym, ∅}, cost proportional to length, and softmax temperature (\alpha). Evaluate whether the PC dynamics produce the same marginals over (A) and (\theta) reported by L&G (posteriors concentrated around “significantly greater than average” yet still vague).  
2. **Context sensitivity:** Shift the prior mean/variance (comparison class) and show corresponding shifts in (\theta) and truth judgments, as in L&G’s Figure 7. 
3. **Sorites:** Compute the probabilities of inductive premises under two readings (material‑conditional and Adams’ Thesis (P(B\mid A))), and under L&G’s “free‑variable in the conditional” interpretation that conditions on a cooperative assertion. The target pattern is high‑probability premises with a low‑probability absurd conclusion.  

**Work package 2 — Extend to nouns.**
I will reuse the “free‑parameter” trick at the semantic interface and the same RSA‑PC inference loop. Two noun types:

* **Thresholded nouns (soritical):** Introduce a latent boundary (\theta_N) over a salient scalar (e.g., harmfulness for *weapon*, age for *child*). Truth = (\mu_N(x)>\theta_N). Infer ((A,\theta_N)) under RSA‑PC from uses like “That is a weapon,” predicting graded borderline membership and sorites‑like tolerance. (Direct analogue of the adjective case.) 
* **Prototype/region nouns (polythetic):** Represent categories as regions in a conceptual space with latent prototype (\mu), dimension weights (w), and tolerance (\tau). Truth ≈ (\text{sim}(x,\mu;w)>\tau). Treat (V={\mu,w,\tau}) as free variables inferred in the RSA‑PC loop; predict context‑sensitive category boundaries and gradedness when priors over features or QUD vary. (Complements L&G’s note that non‑scalar vagueness likely requires such extra structure.) 

**Methodological details (shared across WP1–2).**

* **Generative assumptions.** QUD‑relative utility; cost ~ utterance length; ALT sets tailored to each domain (e.g., {*cup*, *bowl*, ∅}). Priors over degrees/features set from published norms or simple Gaussians/Beta distributions; uniform priors on free semantic variables unless data suggest otherwise.  
* **Recognition dynamics.** PC message passing with precision scheduling; softmax likelihood for discrete (u). Convergence diagnostics (free‑energy decrease), and ablations varying (\alpha), costs, and ALT to test robustness and identifiability. 
* **Evaluation.** (i) **Judgment‑level:** Posterior predictive fits to graded truth/acceptability and borderline membership (Eq. 32‑style integrals). (ii) **Process‑level (exploratory):** Predict how manipulations that tighten priors (e.g., explicit comparison classes, intensifiers) should speed convergence and increase confidence, aligning with precision‑based interpretations of reading time and N400 effects.  

**Expected contributions.**

1. A unifying account that ties RSA’s explanatory successes in vagueness to an explicit, neurally‑plausible inference mechanism (PC). 2) A portable implementation (adjectives → nouns) showing that pragmatic inference over free semantic parameters generalizes beyond degrees. 3) Concrete, testable process‑level predictions (confidence, speed) that are absent in a purely computational‑level RSA story.  

**Feasibility & plan.**

* **Weeks 1–2:** Reproduce baseline RSA simulations (static inference) and align notation/datasets. 
* **Weeks 3–5:** Implement PC inference for the RSA generative model; validate on adjective case. 
* **Weeks 6–8:** Systematic parameter sweeps (priors, ALT, costs, (\alpha)); replicate context and sorites results.  
* **Weeks 9–10:** Extend to nouns (thresholded, then prototype/region); compare models. 
* **Weeks 11–12:** Write‑up; prepare code appendix and figures matching L&G’s diagnostics. 

**Risks & mitigations.**

* *Discrete utterances in PC:* use a categorical/softmax node (or Gumbel‑softmax for gradients).
* *Identifiability of (\theta) vs prior scale:* anchor priors from norms; report sensitivity; include ALT/cost ablations.
* *Noun model complexity:* start with scalar/thresholded nouns; prototype/region as stretch target. 

**Fit for supervision.**
The project sits at the intersection of semantics/pragmatics, cognitive modeling, and psycholinguistics. It is appropriate for supervisors in formal semantics (degree theory, comparison classes), computational pragmatics (RSA), or cognitive neuroscience of language (predictive processing).  

---

**One quick choice to tailor this for your department:** would you like the deliverables to include a **small online judgment study** (borderline membership for a handful of items) or to keep the scope **purely modeling/simulation**? Pick one, and I’ll adjust the description and work plan accordingly.
