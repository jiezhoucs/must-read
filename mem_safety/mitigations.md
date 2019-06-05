# Security Mitigations against Memory Corruption.

## Shadow Stack

[RAD: A Compile-Time Solution to Buffer Overflow
Attacks](https://static.aminer.org/pdf/PDF/000/296/610/rad_a_compile_time_solution_to_buffer_overflow_attacks.pdf)
[ICDCS'01]

[Using DISE to Protect Return Addresses from
Attack](http://www.elewis.net/papers/wassa04.pdf) [WASSA'05]

[Transparent Runtime Shadow Stack: Protection against malicious return address
modifications](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.120.5702&rep=rep1&type=pdf)
[Unknown'08]

[The Performance Cost of Shadow Stacks and Stack
Canaries](https://people.eecs.berkeley.edu/~daw/papers/shadow-asiaccs15.pdf)
[AsiaCCS'15]

[SoK: Shining Light on Shadow
Stacks](http://nebelwelt.net/publications/files/19Oakland.pdf) [Oakland'19]


## Randomization and Probabilistic Approaches

[Address Obfuscation: an Efficient Approach to Combat a Broad Range of Memory
Error
Exploits](https://www.usenix.org/legacy/event/sec03/tech/full_papers/bhatkar/bhatkar.pdf)
[USS'03]

[On the Effectiveness of Address-Space
Randomization](http://delivery.acm.org/10.1145/1040000/1030124/p298-shacham.pdf?ip=128.151.150.2&id=1030124&acc=ACTIVE%20SERVICE&key=7777116298C9657D%2EDC6AD36C640314EC%2E6B689847FE614015%2E4D4702B0C3E38B35&__acm__=1554590191_6dfbc3b2e74b6f7ce35d6c8d457f378c)
[CCS'04]

[DieHard: Probabilistic Memory Safety for Unsafe
Languages](https://scholarworks.umass.edu/cgi/viewcontent.cgi?article=1086&context=cs_faculty_pubs)
[PLDI'06]


## Control Flow Integrity (CFI)

[Securing software by enforcing data-flow
integrity](https://www.microsoft.com/en-us/research/wp-content/uploads/2006/11/dfiOSDI.pdf)
[OSDI'06]

[Combining Control-Flow Integrity and Static Analysis for Efficient and
Validated Data
Sandboxing](http://www.cse.psu.edu/~gxt29/papers/cfiDataSandboxing.pdf) [CCS'11]

[Practical Control Flow Integrity & Randomization for Binary
Executables](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6547133)
[Oakland'13]

[Control Flow Integrity for COTS
Binaries](https://www.usenix.org/system/files/conference/usenixsecurity13/sec13-paper_zhang.pdf)
[USS'13]

[Enforcing Forward-Edge Control-Flow Integrity in GCC & LLVM](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/42808.pdf) [USS'14]

[Stitching the Gadgets: On the Ineffectiveness of Coarse-Grained Control-Flow 
Integrity Protection](https://www.usenix.org/system/files/conference/usenixsecurity14/sec14-paper-davi.pdf) [USS'14]

[Counterfeit Object-oriented
Programming](https://www.syssec.ruhr-uni-bochum.de/media/emma/veroeffentlichungen/2015/03/28/COOP-Oakland15.pdf)
[Oakland'15]

[Control-Flow Bending: On the Effectiveness of Control-Flow
Integrity](http://nebelwelt.net/publications/files/15SEC.pdf) [USS'15]

[Per-Input Control-Flow
Integrity](http://www.cse.psu.edu/~gxt29/papers/picfi.pdf) [CCS'15]

[Control Jujutsu: On the Weaknesses of Fine-Grained Control Flow
Integrity](https://people.csail.mit.edu/fanl/papers/jujutsu-ccs15.pdf) [CCS'15]

[Losing Control: On the Effectiveness of Control-Flow Integrity under Stack
Attacks](https://www.ics.uci.edu/~perl/ccs15_stackdefiler.pdf) [CCS'15]

[Control-Flow Integrity: Precision, Security, and
Performance](https://www.sba-research.org/wp-content/uploads/publications/CFI_brunthaler.pdf)
[CSUR'17]

[Towards Interface-Driven COTS Binary
Hardening](https://www.utdallas.edu/~hamlen/xu18feast.pdf) [FEAST'18]

[Enforcing Unique Code Target Property for Control-Flow
Integrity](https://www.cc.gatech.edu/~hhu86/papers/ucfi.pdf) [CCS'18]


## Sandboxing / Software Fault Isolation (SFI) 

[SASI Enforcement of Security Policies: A
Retrospective](https://www.cs.cornell.edu/fbs/publications/sasiNSPW.ps)
[NSPW'99]

[Evaluating SFI for a CISC
Architecture](http://groups.csail.mit.edu/pag/pubs/pittsfield-usenix2006.pdf)
[USS'06]

[Vx32: Lightweight User-level Sandboxing on the
x86](https://pdfs.semanticscholar.org/1ce0/4e9007a26a21104b8bf4aedc81654463119a.pdf?_ga=2.45664096.598654028.1546450325-1063382891.1546450325)
[ATC'08]

[Native Client: A Sandbox for Portable, Untrusted x86 Native
Code](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/34913.pdf)
[Oakland'09]

[Fast Byte-Granularity Software Fault
Isolation](https://www.sigops.org/s/conferences/sosp/2009/papers/castro-sosp09.pdf)
[SOSP'09]

[Adapting Software Fault Isolation to Contemporary CPU
Architectures](https://www.usenix.org/legacy/events/sec10/tech/full_papers/Sehr.pdf)
[USS'10]

[Safe Loading - A Foundation for Secure Execution of Untrusted
Programs](http://hexhive.epfl.ch/publications/files/12Oakland.pdf) [Oakland'12]

## Others

[StackGuard: Automatic Adaptive Detection and Prevention of Buffer-Overflow
Attacks](https://www.usenix.org/legacy/publications/library/proceedings/sec98/full_papers/cowan/cowan.pdf)
[USS'98]

[PointGuardTM: Protecting Pointers From Buffer Overflow
Vulnerabilities](https://www.usenix.org/legacy/event/sec03/tech/full_papers/cowan/cowan.pdf)
[USS'03]

[Securing software by enforcing data-flow integrity](https://timharris.uk/papers/2006-osdi.pdf) [OSDI'06]

[Code-Pointer Integrity](https://dslab.epfl.ch/pubs/cpi.pdf) [OSDI'14]

[Missing the Point(er): On the Effectiveness of Code Pointer
Integrity](http://web.mit.edu/ha22286/www/papers/Oakland15.pdf) [Oakland'15]

