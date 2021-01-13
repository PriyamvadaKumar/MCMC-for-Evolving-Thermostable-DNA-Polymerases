# MCMC-for-Evolving-Thermostable-DNA-Polymerases
Markov Chain Monte Carlo Method for Evolving Thermostable DNA Polymerases( using Gibbs and Metropolis samplers) to perform directed evolution in Taq Polymerase to increase thermostability and maintain sequence similarity. Compared model performance with a genetic algorithm (based on natural selection)which is currently used to simulate directed evolution ​in-silico.


Our project aims to iteratively evolve thermostability in a protein encoded from a starting amino acid sequence. Markov Chain Monte Carlo simulation (MCMC) is one such method of iteratively sampling a variable to track its evolution over time. We will implement MCMC as a means to directly evolve thermostability in a starting gene sequence, and compare its performance against random mutagenesis. In theory, MCMC could provide modifications that are more informed than random mutagenesis, as transition probabilities could
be guided by desirable metrics, such as increases in thermostability and proximity to active sites. An algorithm for in silico protein engineering could be applied in a variety of settings to cut down on time and resources spent doing so ​in vitro.​
Traditionally, genetic algorithms have been used for simulating evolution, as their implementation is largely based on Charles Darwin’s theory of natural selection. However, not as much work exists on applications of MCMC to protein engineering via directed evolution.



If thermostability(new) > thermostability(old), and the change doesn't take place in an active site , then we transition.
If thermostability (new) < thermostability(old), and the change doesn't take place in an active site, then we transition with some probability based on the ratio of thermostability(new) / thermostabilty(old).

For example, if we start with thermostability(old) = 0.6, and make some change that results in thermostability(new) = 0.7, then we transition. If thermostability(new) = 0.5, then we transition with probability binomial(0.5/0.6).


From our implementation, MCMC was unable to consistently increase thermostability and preserve sequence similarity. This is likely due to the fact that each step of Gibbs sampling “wandered” through 100 steps of sequence space before landing on a final candidate, resulting in each step of Gibbs sampling being more likely to deviate from the original sequence and not monotonically increase in thermostability. Our implementation of the genetic algorithm, on the other hand, allowed for consistent selection of the largest increase in thermostability across each of the 100 generations, with one single opportunity to deviate from the starting sequence (rather than 100).
To improve MCMC performance, we could use a single sampler, rather than Metropolis in Gibbs. This would allow for substantially less exploration of sequence space at each step, potentially resulting in the algorithm not taking steps that significantly deviate from the original sequence without improving thermostability.
