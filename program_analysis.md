# Program Analysis

[JACM'76] [Global Data Flow Analysis and Iterative Algorithms]

[POPL'77] [Abstract Interpretation: A Unified Latice Model for Static Analysis
of Programs by Construction or Approximation of
Fixpoints](https://courses.cs.washington.edu/courses/cse503/10wi/readings/p238-cousot.pdf)

[TOPLAS'87] [The Program Dependence Graph and Its Use in
Optimization](https://www.cs.utexas.edu/~pingali/CS395T/2009fa/papers/ferrante87.pdf)

[TOPLAS'88] [Interprocedural Slicing Using Dependence
Graphs](https://cs.gmu.edu/~white/CS640/10.1.1.50.4405.pdf)

[CC'96] [Effective Representation of Aliases and Indirect Memory Operations
in SSA Form](https://link.springer.com/content/pdf/10.1007/3-540-61053-7_66.pdf)

[TOPLAS'94] [Efficient Computation of Interprocedural Definition-Use
Chains](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.72.8860&rep=rep1&type=pdf)

[POPL'95] [Precise Interprocedural Dataflow Analysis via Graph Reachability](https://dl.acm.org/doi/pdf/10.1145/199448.199462)

[Oakland'01] [Intrusion Detection via Static
Analysis](http://www.csl.sri.com/users/ddean/papers/oakland01.pdf)

[PLDI'05] [Automatic Pool Allocation: Improving Performance by Controlling Data
Structure Layout in the Heap](https://llvm.org/pubs/2005-05-21-PLDI-PoolAlloc.pdf)

[ISSTA'12] [Static Memory Leak Detection Using Full-Sparse Value-Flow
Analysis](https://yuleisui.github.io/publications/issta12.pdf)

[ACMComm'15] [In defense of soundiness: a
manifesto](https://dl.acm.org/citation.cfm?doid=2728770.2644805)

[CC'16] [SVF: Interprocedural Static Value-Flow Analysis in
LLVM](https://yuleisui.github.io/publications/cc16.pdf)

[ACMCompSurvey'16] [Heap Abstractions for Static
Analysis](https://dl.acm.org/doi/abs/10.1145/2931098)

[PLDI'18] [PMAF: An Algebraic Framework for Static Analysis of Probabilistic
Programs](https://www.cs.cmu.edu/~diw3/papers/WangHR17.pdf)
[[note](notes/pa/pmaf.md)]

[CGO'19] [Function Merging by Sequence
Alignment](http://homepages.inf.ed.ac.uk/hleather/publications/2019_functionmergesequencealign_cgo2019.pdf)

[ASPLOS'21] [Who’s Debugging the Debuggers? Exposing Debug Information Bugs in
Optimized Binaries](https://download.vusec.net/papers/debug2_asplos21.pdf)

[DAC'21] [Towards Reliable Spatial Memory Safety for Embedded Software by
Combining Checked C with Concolic
Testing](http://www.informatik.uni-bremen.de/agra/doc/konf/DAC-2021-CheckedC-Concolic-Testing.pdf)


## Pointer Analysis

[POPL'90] [Pointer-induced Aliasing: A Problem
Classification](https://www.cmi.ac.in/~madhavan/courses/program-analysis-2008/papers/landi91-ptr-analysis-popl.pdf)

[LOPLAS'92] [Undecidability of Static Analysis](https://dl.acm.org/doi/pdf/10.1145/161494.161501)

[POPL'93] [Efficient Flow-Sensitive Interprocedural Computation of Pointer-Induced Aliases and Side Effects](https://dl.acm.org/doi/pdf/10.1145/158511.158639)

[PLID'94] [Context-Sensitive Interprocedural Points-to Analysis in the Presence of Function Pointers](https://dl.acm.org/doi/pdf/10.1145/773473.178264)

[TOPLAS'94] [The Undecidability of Aliasing](http://web.cs.ucla.edu/~palsberg/course/cs232/papers/ramalingam-toplas94.pdf)

[PLID'95] [Efficient Context-Sensitive Pointer Analysis for C Programs](https://dl.acm.org/doi/pdf/10.1145/1290520.1290524)

[POPL'96] [Points-to Analysis in Almost Linear
Time](https://www.cs.cornell.edu/courses/cs711/2005fa/papers/steensgaard-popl96.pdf)

[SAS'97] [The Effects of the Precision of Pointer Analysis](https://research.cs.wisc.edu/wpis/papers/sas97.pdf)

[POPL'97] [Fast and Accurate Flow-insensitive Points-to
Analysis](https://dl.acm.org/doi/pdf/10.1145/263699.263703)

[TOPLAS'97] [Precise Flow-Insensitive May-Alias Analysis is
NP-Hard](https://dl.acm.org/doi/pdf/10.1145/239912.239913)

[PLDI'98] [Type-Based Alias
Analysis](http://web.cs.ucla.edu/~palsberg/tba/papers/diwan-mckinley-moss-pldi98.pdf)

[TOPLAS'99] [Interprocedural Pointer Alias Analysis](https://dl.acm.org/doi/pdf/10.1145/325478.325519)

[OOPSLA'99] [Compositional Pointer and Escape Analysis for Java
Programs](https://people.csail.mit.edu/rinard/paper/oopsla99.pdf)

[PLDI'00] [Unification Based Pointer Analysis with
Directional](http://web.cs.ucla.edu/~palsberg/course/purdue/cs661/F01/papers/das-pldi00.pdf)

[ISSTA'00] [Which Pointer Analysis Should I Use?](https://logic.pdmi.ras.ru/~yura/of/alias.pdf)

[PLDI'01] [Incrementalized Pointer and Escape
Analysis](https://people.csail.mit.edu/rinard/paper/pldi01.full.pdf)

[PLDI'01] [Demand-Driven Pointer
Analysis](https://dl.acm.org/doi/10.1145/381694.378802#:~:text=16-,ABSTRACT,a%20program%20or%20program%20component.&text=Specifically%2C%20we%20describe%20a%20demand,%2Dinsensitive%20points%2Dto%20analysis.)

[PASTE'01] [Pointer Analysis: Haven’t We
Solved This Problem Yet?](https://dl.acm.org/doi/pdf/10.1145/379605.379665)

[PASTE'04] [Importance of Heap Specialization in Pointer
Analysis](http://impact.crhc.illinois.edu/shared/papers/paste-04-nystrom.pdf)

[PLDI'07] [The Ant and the Grasshopper: Fast and Accurate Pointer Analysis
for Millions of Lines of Code](https://www.cs.utexas.edu/~lin/papers/pldi07.pdf)

[PLDI'07] [Making Context-sensitive Points-to Analysis with Heap Cloning
Practical For The Real World](http://llvm.org/pubs/2007-06-10-PLDI-DSA.pdf)

[SAS'07] [Exploiting pointer and location equivalence to optimize pointer
analysis](https://hardekbc.github.io/files/hardekopf07exploiting.pdf)

[POPL'08] [Demand-Driven Alias Analysis for
C](https://www.cs.cornell.edu/~xinz/papers/alias-popl08.pdf)

[CGO'09] [Wave Propagation and Deep Propagation for Pointer
Analysis](http://compilers.cs.ucla.edu/fernando/publications/papers/CGO09.pdf)

[POPL'09] [Semi-Sparse Flow-Sensitive Pointer
Analysis](https://sites.cs.ucsb.edu/~benh/research/papers/hardekopf09semisparse.pdf)

[CGO'11] [Flow-Sensitive Pointer Analysis for Millions of Lines of
Code](https://www.cs.utexas.edu/users/lin/papers/cgo11.pdf)

[Book'15] [Pointer Analysis](https://yanniss.github.io/points-to-tutorial15.pdf)

[SAS'16] [Structure-Sensitive Points-To Analysis for C and C++](https://yanniss.github.io/cclyzer-sas16.pdf)


## Information Flow, Symbolic Execution, and Taint Analysis

[USS'04] [Understanding Data Lifetime via Whole System
Simulation](https://benpfaff.org/papers/taint.pdf)

[ASPLOS'04] [Secure Program Execution via Dynamic Information Flow
Tracking](http://csg.csail.mit.edu/pubs/memos/Memo-467/memo-467.pdf)

[NDSS'05] [Dynamic Taint Analysis for Automatic Detection, Analysis,
and Signature Generation of Exploits on Commodity
Software](https://people.eecs.berkeley.edu/~dawnsong/papers/taintcheck.pdf)

[SOSP'05] [Vigilante: End-to-End Containment of Internet
Worms](http://rowstron.azurewebsites.net/MS/VigilanteSOSP.pdf)

[CSUR'18] [A Survey of Symbolic Execution
Techniques](https://dl.acm.org/doi/10.1145/318265)


## Debugging
[S4DC'12] [A Review Of Reverse
Debugging](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.338.3420&rep=rep1&type=pdf)

[OSDI'18] [REPT: Reverse Debugging of Failures in Deployed
Software](https://www.microsoft.com/en-us/research/uploads/prod/2018/08/osdi18-final211.pdf)

## Fuzzing

[Oakland'16] [LAVA: Large-scale Automated Vulnerability
Addition](https://www.andreamambretti.com/files/papers/oakland2016_lava.pdf)

[PLDI'05] [DART: Directed Automated Random
Testing](https://web.eecs.umich.edu/~weimerw/2011-6610/reading/p213-godefroid.pdf)

[ACMQueue'12] [SAGE: Whitebox Fuzzing for Security
Testing](https://queue.acm.org/detail.cfm?id=2094081)
