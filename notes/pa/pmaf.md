# Title and Author(s)

### Category and Keywords
probabilistic programming; static analysis;

### What problem this paper tried to solve?
How to automatically establish that a probabilistic program satisfied some
property p.

### Why is the problem important?
Probabilistic programming provides a rich framework for implementing randomized
algorithms, cryptography protocols, and machine learning algorithms.

### What is this paper's solution to the problem?
It provides a framework, called PMAF (Pre-Markov Algebra Framework) for
designing, implementing, and providing the correctness of static analysis of
probabilistic programs.

### What are the strengths of this paper?
- PMAF can handle challenging features such as recursion, unstructured
control-flow, divergence, nondeterminism, and continuous distributions.

- One novelty of PMAF is that it's based on a semantics formulated in terms of
control-flow hypergraph.

- The main advantage of PMAF is that you don't need to create a new analysis from
scratch; you only need to instantiate PMAF with the implementation of a new
pre-Markov algebra.

- The PMAF implementation supplies common parts of different static analysis of
  probabilistic programs.

- Any improvements made to the PMAF implementation immediately translates into
  improvements to all of its instantiations.

### What are the limitations of this paper?

### What are other solutions and what are the most relevant works?

### What is the take-away message from this paper?

### notes on the hypergraph analysis
- Nondeterminism is modeled by collections of such distributions.
- The semantics of a node is a summary of computation that continues from the 
node.
- The hyper-graph analysis is formulated by an equation system
