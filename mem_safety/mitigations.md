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


[CCS'04] [On the Effectiveness of Address-Space
Randomization](https://dl.acm.org/citation.cfm?id=1030124)

[PLDI'06] [DieHard: Probabilistic Memory Safety for Unsafe
Languages](https://scholarworks.umass.edu/cgi/viewcontent.cgi?article=1086&context=cs_faculty_pubs)


## Control Flow Integrity (CFI)

[OSDI'06] [Securing software by enforcing data-flow
integrity](https://www.microsoft.com/en-us/research/wp-content/uploads/2006/11/dfiOSDI.pdf)

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

[USS'14] [Stitching the Gadgets: On the Ineffectiveness of Coarse-Grained
Control-Flow Integrity
Protection](https://www.usenix.org/system/files/conference/usenixsecurity14/sec14-paper-davi.pdf) 

[Oakland'15] [Counterfeit Object-oriented
Programming](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2015/03/28/COOP-Oakland15.pdf)

[USS'15] [Control-Flow Bending: On the Effectiveness of Control-Flow
Integrity](http://nebelwelt.net/publications/files/15SEC.pdf) 

[CCS'15] [Per-Input Control-Flow
Integrity](http://www.cse.psu.edu/~gxt29/papers/picfi.pdf) 

[CCS'15] [Control Jujutsu: On the Weaknesses of Fine-Grained Control Flow
Integrity](https://people.csail.mit.edu/fanl/papers/jujutsu-ccs15.pdf) 

[CCS'15] [Losing Control: On the Effectiveness of Control-Flow Integrity under Stack
Attacks](https://www.ics.uci.edu/~perl/ccs15_stackdefiler.pdf) 

[CSUR'17] [Control-Flow Integrity: Precision, Security, and
Performance](https://www.sba-research.org/wp-content/uploads/publications/CFI_brunthaler.pdf)

[FEAST'18] [Towards Interface-Driven COTS Binary
Hardening](https://www.utdallas.edu/~hamlen/xu18feast.pdf) 

[CCS'18] [Enforcing Unique Code Target Property for Control-Flow
Integrity](https://www.cc.gatech.edu/~hhu86/papers/ucfi.pdf) 


## Sandboxing / Software Fault Isolation (SFI) 

[NSPW'99] [SASI Enforcement of Security Policies: A
Retrospective](https://www.cs.cornell.edu/fbs/publications/sasiNSPW.ps)

[USS'06] [Evaluating SFI for a CISC
Architecture](http://groups.csail.mit.edu/pag/pubs/pittsfield-usenix2006.pdf)

[ATC'08] [Vx32: Lightweight User-level Sandboxing on the
x86](https://pdfs.semanticscholar.org/1ce0/4e9007a26a21104b8bf4aedc81654463119a.pdf?_ga=2.45664096.598654028.1546450325-1063382891.1546450325)

[Oakland'09] [Native Client: A Sandbox for Portable, Untrusted x86 Native
Code](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/34913.pdf)

[SOSP'09] [Fast Byte-Granularity Software Fault
Isolation](https://www.sigops.org/s/conferences/sosp/2009/papers/castro-sosp09.pdf)

[USS'10] [Adapting Software Fault Isolation to Contemporary CPU
Architectures](https://www.usenix.org/legacy/events/sec10/tech/full_papers/Sehr.pdf)

[Oakland'12] [Safe Loading - A Foundation for Secure Execution of Untrusted
Programs](http://hexhive.epfl.ch/publications/files/12Oakland.pdf) 


## Others

[USS'98] [StackGuard: Automatic Adaptive Detection and Prevention of
Buffer-Overflow
Attacks](https://www.usenix.org/legacy/publications/library/proceedings/sec98/full_papers/cowan/cowan.pdf)

[USS'03] [PointGuardTM: Protecting Pointers From Buffer Overflow
Vulnerabilities](https://www.usenix.org/legacy/event/sec03/tech/full_papers/cowan/cowan.pdf)

[OSDI'06] [Securing software by enforcing data-flow
integrity](https://timharris.uk/papers/2006-osdi.pdf) 

[OSDI'14] [Code-Pointer Integrity](https://dslab.epfl.ch/pubs/cpi.pdf) 

[Oakland'15] [Missing the Point(er): On the Effectiveness of Code Pointer
Integrity](http://web.mit.edu/ha22286/www/papers/Oakland15.pdf) 
