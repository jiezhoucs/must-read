# Security Mitigations against Memory Corruption.

## Shadow Stack

[ICDCS'01] [RAD: A Compile-Time Solution to Buffer Overflow
Attacks](https://static.aminer.org/pdf/PDF/000/296/610/rad_a_compile_time_solution_to_buffer_overflow_attacks.pdf)

[WASSA'05] [Using DISE to Protect Return Addresses from
Attack](http://www.elewis.net/papers/wassa04.pdf) 

[Unknown'08] [Transparent Runtime Shadow Stack: Protection against malicious
return address
modifications](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.120.5702&rep=rep1&type=pdf)

[AsiaCCS'15] [The Performance Cost of Shadow Stacks and Stack
Canaries](https://people.eecs.berkeley.edu/~daw/papers/shadow-asiaccs15.pdf)

[Oakland'19] [SoK: Shining Light on Shadow
Stacks](http://nebelwelt.net/publications/files/19Oakland.pdf) 


## Randomization and Probabilistic Approaches

[USS'03] [Address Obfuscation: an Efficient Approach to Combat a Broad Range of
Memory Error
Exploits](https://www.usenix.org/legacy/event/sec03/tech/full_papers/bhatkar/bhatkar.pdf)

[Sec'05] [Efficient Techniques for Comprehensive Protection from Memory
Error
Exploits](https://www.usenix.org/legacy/event/sec05/tech/full_papers/bhatkar/bhatkar.pdf)

[CCS'04] [On the Effectiveness of Address-Space
Randomization](https://dl.acm.org/citation.cfm?id=1030124)


## Control Flow Integrity (CFI)

[TISSEC'07] [Control-Flow Integrity Principles, Implementations, and 
Applications](https://cseweb.ucsd.edu/~dstefan/cse127-fall20/papers/abadi:cfi.pdf)

[CCS'11] [Combining Control-Flow Integrity and Static Analysis for Efficient and
Validated Data
Sandboxing](http://www.cse.psu.edu/~gxt29/papers/cfiDataSandboxing.pdf)

[Oakland'13] [Practical Control Flow Integrity & Randomization for Binary
Executables](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6547133)

[USS'13] [Control Flow Integrity for COTS
Binaries](https://www.usenix.org/system/files/conference/usenixsecurity13/sec13-paper_zhang.pdf)

[PLDI'14] [Modular Control-Flow
Integrity](http://www.cse.psu.edu/~gxt29/papers/mcfi.pdf)

[USS'14] [Enforcing Forward-Edge Control-Flow Integrity in GCC &
LLVM](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/42808.pdf)

[Oakland'15] [Counterfeit Object-oriented
Programming](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2015/03/28/COOP-Oakland15.pdf)

[CCS'15] [Per-Input Control-Flow
Integrity](http://www.cse.psu.edu/~gxt29/papers/picfi.pdf)

[CSUR'17] [Control-Flow Integrity: Precision, Security, and
Performance](https://www.sba-research.org/wp-content/uploads/publications/CFI_brunthaler.pdf)

[FEAST'18] [Towards Interface-Driven COTS Binary
Hardening](https://www.utdallas.edu/~hamlen/xu18feast.pdf)

[CCS'18] [Enforcing Unique Code Target Property for Control-Flow
Integrity](https://www.cc.gatech.edu/~hhu86/papers/ucfi.pdf)

[Sec'21] [VScape: Assessing and Escaping Virtual Call
Protections](https://www.usenix.org/system/files/sec21fall-chen-kaixiang.pdf)

[RAID'23] [Renewable Just-In-Time Control-Flow
Integrity](https://dl.acm.org/doi/abs/10.1145/3607199.3607239)


## Others

[USS'98] [StackGuard: Automatic Adaptive Detection and Prevention of
Buffer-Overflow
Attacks](https://www.usenix.org/legacy/publications/library/proceedings/sec98/full_papers/cowan/cowan.pdf)

[USS'03] [PointGuard: Protecting Pointers From Buffer Overflow
Vulnerabilities](https://www.usenix.org/legacy/event/sec03/tech/full_papers/cowan/cowan.pdf)

[OSDI'06] [Securing software by enforcing data-flow
integrity](https://timharris.uk/papers/2006-osdi.pdf) 

[OSDI'06] [XFI: Software Guards for System Address Spaces](https://www.usenix.org/legacy/event/osdi06/tech/full_papers/erlingsson/erlingsson.pdf)
