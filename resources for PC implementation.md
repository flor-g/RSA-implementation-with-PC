### Foundations & cortical architecture

* **Core hierarchical scheme.** PC posits hierarchies of prediction units sending top-down predictions and error units sending bottom-up residuals; the classic instantiation explains extra-classical receptive-field effects and provides explicit update equations (Rao & Ballard, 1999). 
* **Unified cortical response theory.** PC is embedded in the free-energy/variational framing, linking evoked responses, inference, and learning (Friston, 2005; Friston, 2010). 
* **Canonical microcircuits.** Laminar feedforward/feedback asymmetries and frequency-specific channels (e.g., gamma vs. beta) map onto predictive vs. error pathways (Bastos et al., 2012). 

### Tutorials & mathematical guides 

* **Step-by-step derivations.** Accessible introductions derive recognition dynamics, precision weighting, and learning rules under the free-energy principle—handy for writing code (Bogacz, 2017; Buckley, Kim, McGregor, & Seth, 2017). 
* **Algorithmic variants.** A systematic review compares PC algorithms and clarifies what “predictive coding” refers to across implementations (Spratling, 2017). 

### Learning rules & links to backpropagation

* **Local Hebbian PC ≈ backprop.** A predictive-coding network can approximate error backpropagation using only local plasticity (Whittington & Bogacz, 2017). 
* **Exact results and general graphs.** Under specific conditions, PC can implement *exact* backprop in MLPs and extend to CNNs/RNNs; further, PC converges to backprop on arbitrary computation graphs and ships with recipes to translate ML architectures (Song, Lukasiewicz, Xu, & Bogacz, 2020; Salvatori, Song, Lukasiewicz, Bogacz, & Xu, 2021; Millidge, Tschantz, & Buckley, 2020). 

### Deep architectures & runnable code

* **PredNet.** A deep recurrent convolutional network inspired by PC for next-frame video prediction; paper and open-source implementation (Lotter, Kreiman, & Cox, 2016/2017). 
* **PC ≈ BP codebases.** Public repos reproduce results for PC-as-backprop on arbitrary computation graphs and provide reference implementations for CNNs/RNNs (Millidge et al., 2020; community implementations of Whittington & Bogacz, 2017). 

---

## References 

Bastos, A. M., Usrey, W. M., Adams, R. A., Mangun, G. R., Fries, P., & Friston, K. J. (2012). Canonical microcircuits for predictive coding. *Neuron, 76*(4), 695–711. [https://doi.org/10.1016/j.neuron.2012.10.038](https://doi.org/10.1016/j.neuron.2012.10.038) ([Cell][3])

Bogacz, R. (2017). A tutorial on the free-energy framework for modelling perception and learning. *Journal of Mathematical Psychology, 76*, 198–211. [https://doi.org/10.1016/j.jmp.2015.11.003](https://doi.org/10.1016/j.jmp.2015.11.003) ([mrcbndu.ox.ac.uk][4])

Buckley, C. L., Kim, C. S., McGregor, S., & Seth, A. K. (2017). The free energy principle for action and perception: A mathematical review. *Journal of Mathematical Psychology, 81*, 55–79. [https://doi.org/10.1016/j.jmp.2017.09.004](https://doi.org/10.1016/j.jmp.2017.09.004) ([ScienceDirect][10])

Friston, K. (2005). A theory of cortical responses. *Philosophical Transactions of the Royal Society B: Biological Sciences, 360*(1456), 815–836. [https://doi.org/10.1098/rstb.2005.1622](https://doi.org/10.1098/rstb.2005.1622) ([Europe PMC][11])

Friston, K. (2010). The free-energy principle: A unified brain theory? *Nature Reviews Neuroscience, 11*(2), 127–138. [https://doi.org/10.1038/nrn2787](https://doi.org/10.1038/nrn2787) ([SCIRP][12])

Lotter, W., Kreiman, G., & Cox, D. (2017). Deep predictive coding networks for video prediction and unsupervised learning. *International Conference on Learning Representations (ICLR).* (Original arXiv preprint 2016). [https://arxiv.org/abs/1605.08104](https://arxiv.org/abs/1605.08104) ([arXiv][8])

Millidge, B., Tschantz, A., & Buckley, C. L. (2020). Predictive coding approximates backprop along arbitrary computation graphs. *arXiv preprint* arXiv:2006.04182. [https://arxiv.org/abs/2006.04182](https://arxiv.org/abs/2006.04182) ([arXiv][13])

Rao, R. P. N., & Ballard, D. H. (1999). Predictive coding in the visual cortex: A functional interpretation of some extra-classical receptive-field effects. *Nature Neuroscience, 2*(1), 79–87. [https://doi.org/10.1038/4580](https://doi.org/10.1038/4580) ([Department of Computer Science][1])

Salvatori, T., Song, Y., Lukasiewicz, T., Bogacz, R., & Xu, Z. (2021). Predictive coding can do exact backpropagation on convolutional and recurrent neural networks. *arXiv preprint* arXiv:2103.03725. [https://arxiv.org/abs/2103.03725](https://arxiv.org/abs/2103.03725) ([arXiv][14])

Song, Y., Lukasiewicz, T., Xu, Z., & Bogacz, R. (2020). Can the brain do backpropagation?—Exact implementation of backpropagation in predictive coding networks. *Advances in Neural Information Processing Systems, 33*, 22566–22579. [https://proceedings.neurips.cc/paper/2020/hash/fec87a37cdeec1c6ecf8181c0aa2d3bf-Abstract.html](https://proceedings.neurips.cc/paper/2020/hash/fec87a37cdeec1c6ecf8181c0aa2d3bf-Abstract.html) ([NeurIPS Proceedings][7])

Spratling, M. W. (2017). A review of predictive coding algorithms. *Neural Networks, 68*, 60–75. [https://doi.org/10.1016/j.neunet.2015.09.005](https://doi.org/10.1016/j.neunet.2015.09.005) ([ScienceDirect][5])

**code links:** PredNet code (GitHub): ([GitHub][15]); PC≈BP code (GitHub): ([GitHub][9]).

[1]: https://www.cs.utexas.edu/~dana/nn.pdf? "Predictive coding in the visual cortex: a functional interpretation of ..."
[2]: https://www.fil.ion.ucl.ac.uk/~karl/A%20theory%20of%20cortical%20responses.pdf? "A theory of cortical responses"
[3]: https://www.cell.com/neuron/fulltext/S0896-6273%2812%2900959-2? "Canonical Microcircuits for Predictive Coding: Neuron"
[4]: https://www.mrcbndu.ox.ac.uk/sites/default/files/pdf_files/Bogacz%202017_J%20Math%20Psychol.pdf? "A tutorial on the free-energy framework for modelling perception and ..."
[5]: https://www.sciencedirect.com/science/article/pii/S027826261530035X? "A review of predictive coding algorithms - ScienceDirect"
[6]: https://www.mrcbndu.ox.ac.uk/sites/default/files/pdf_files/Whittington%20Bogacz%202017_Neural%20Comput.pdf? "An Approximation of the Error Backpropagation Algorithm in a Predictive ..."
[7]: https://proceedings.neurips.cc/paper/2020/hash/fec87a37cdeec1c6ecf8181c0aa2d3bf-Abstract.html? "Can the Brain Do Backpropagation? --- Exact Implementation of ... - NeurIPS"
[8]: https://arxiv.org/abs/1605.08104? "Deep Predictive Coding Networks for Video Prediction and Unsupervised Learning"
[9]: https://github.com/BerenMillidge/PredictiveCodingBackprop? "Code for the paper \"Predictive Coding Approximates Backprop ... - GitHub"
[10]: https://www.sciencedirect.com/science/article/pii/S0022249617300962? "The free energy principle for action and perception: A mathematical review"
[11]: https://europepmc.org/abstract/MED/15937014? "A theory of cortical responses. - Abstract - Europe PMC"
[12]: https://www.scirp.org/reference/referencespapers?referenceid=2539689& "Friston, K. (2005) A Theory of Cortical Responses. Philosophical ..."
[13]: https://arxiv.org/abs/2006.04182? "Predictive Coding Approximates Backprop along Arbitrary Computation Graphs"
[14]: https://arxiv.org/abs/2103.03725? "Predictive Coding Can Do Exact Backpropagation on Convolutional and Recurrent Neural Networks"
[15]: https://github.com/coxlab/prednet? "GitHub - coxlab/prednet: Code and models accompanying \"Deep Predictive ..."
