# Safe C/C++ Implementations

[USENIX-Winter'92] [Purify: Fast Detection of Memory Leaks and Access
Errors](https://pdfs.semanticscholar.org/b2c4/44e8ab6b9bea1072bb0a7dd321543c8520ea.pdf)

[PLDI'94] [Efficient Detection of All Pointer and Array Access
Errors](https://web.eecs.umich.edu/~taustin/papers/PLDI94-safec.pdf)

[AADEBUG'97] [Backwards-compatible bounds checking for arrays and pointers in C
programs](https://www.doc.ic.ac.uk/~phjk/Publications/BoundsCheckingForC.pdf)
[[note](../notes/mem_safety/safe_impl/1997-J_K_Bounds_Check-AADEBUG97.md)]

[FSE'04] [An Efficient and Backwards-Compatible Transformation to Ensure Memory
Safety of C
Programs](http://www.sis.pitt.edu/jjoshi/courses/IS2620/Spring09/Xu.pdf)

[NDSS'04] [A Practical Dynamic Buffer Overflow
Detector](https://suif.stanford.edu/papers/tunji04.pdf)
[[notes](../notes/mem_safety/safe_impl/2004-CRED-NDSS04.md)]

[ACSAC'04] [A Dynamic Technique for Eliminating Buffer Overflow Vulnerabilities
(and Other Memory Errors)](https://www.acsac.org/2004/papers/98.pdf)

[TECS'05] [Memory Safety Without Garbage Collection for Embedded
Applications](https://llvm.org/pubs/2005-02-TECS-SAFECode.pdf)

[PLDI'07] [Valgrind: A Framework for Heavyweight Dynamic Binary
Instrumentation](http://valgrind.org/docs/valgrind2007.pdf)

[PLDI'09] [Implementation of the Memory-safe Full ANSI-C
Compiler](http://delivery.acm.org/10.1145/1550000/1542505/p259-oiwa.pdf?ip=131.107.159.119&id=1542505&acc=ACTIVE%20SERVICE&key=7777116298C9657D%2EDC6AD36C640314EC%2E6B689847FE614015%2E4D4702B0C3E38B35&__acm__=1559361572_68b410a3c3fef73daf2b3c211f8d0d9f)

[PLDI'09] [SoftBound: Highly Compatible and Complete Spatial Memory Safety for
C](http://www.cis.upenn.edu/acg/papers/pldi09_softbound.pdf)

[AsiaCCS'10] [PAriCheck: An Efficient Pointer Arithmetic Checker for C
Programs](http://fort-knox.org/files/paricheck.pdf)

[ToIFaS'11] [Comprehensive and Efficient Protection of Kernel Control
Data](http://people.duke.edu/~tkb13/pubs/KernelControlData.pdf)

[CGO'11] [Practical Memory Checking with Dr.
Memory](https://dl.acm.org/doi/10.5555/2190025.2190067)

[CGO'12] [Light-weight Bounds
Checking](http://seclab.cs.sunysb.edu/seclab/pubs/lbc.pdf)

[ATC'12] [AddressSanitizer: A Fast Address Sanity
Checker](https://www.usenix.org/system/files/conference/atc12/atc12-final39.pdf)

[SPE'13] [MemSafe: ensuring the spatial and temporal memory safety ofC at
runtime](https://onlinelibrary.wiley.com/doi/epdf/10.1002/spe.2105)

[PLAS'15] [Memory-safe Execution of C on a Java
VM](https://chrisseaton.com/plas15/safec.pdf)

[SNAPL'15] [Everything You Want to Know About Pointer-Based
Checking](https://core.ac.uk/download/pdf/62919692.pdf)

[EuroSec'16] [METAlloc: Efficient and Comprehensive Metadata Management
for Software Security
Hardening](https://www.cs.vu.nl/~giuffrida/papers/eurosec-2016.pdf)

[CC'16] [Heap Bounds Protection with Low Fat
Pointers](https://www.comp.nus.edu.sg/~gregory/papers/cc16lowfatptrs.pdf)
[[note](../notes/mem_safety/safe_impl/2016-Low-fat_Ptr_Heap-CC16.md)]

[NDSS'17] [SafeInit: Comprehensive and Practical Mitigation of Uninitialized
Read Vulnerabilities](https://download.vusec.net/papers/safeinit_ndss17.pdf)

[EuroSec'17] [Fast and Generic Metadata Management with Mid-Fat
Pointers](https://www.cs.vu.nl/~giuffrida/papers/midfat_eurosec17.pdf)

[USS'17] [Venerable Variadic Vulnerabilities
Vanquished](https://www.usenix.org/system/files/conference/usenixsecurity17/sec17-biswas.pdf)

[PLDI'18] [EffectiveSan: Type and Memory Error Detection using Dynamically
Typed C/C++](https://arxiv.org/pdf/1710.06125.pdf)

[AsiaCCS'18] [CUP: Comprehensive User-Space Protection for
C/C++](https://nebelwelt.net/files/18AsiaCCS.pdf)
[[note](../notes/mem_safety/safe_impl/2018-CUP-AsiaCCS18.md)]


## Temporal
[DSN'06] [Efficiently Detecting All Dangling Pointer Uses in Production
Servers](https://llvm.org/pubs/2006-DSN-DanglingPointers.pdf)
[[note](../notes/mem_safety/d-a_dan_ptr.md)]

[PLDI'07][Exterminator: Automatically Correcting Memory Errors with High
Probability](https://people.cs.umass.edu/~emery/pubs/pldi028-novark.pdf)

[ISMM'10] [CETS: Compiler-Enforced Temporal Safety for
C](http://www.cis.upenn.edu/acg/papers/ismm10_cets.pdf)

[NDSS'15] [Preventing Use-after-free with Dangling Pointers
Nullification](https://wenke.gtisc.gatech.edu/papers/dangnull.pdf)
[[note](../notes/mem_safety/safe_impl/2015-DANGNULL-NDSS15.md)]

[NDSS'15] [FreeSentry: Protecting Against Use-After-Free Vulnerabilities Due to
Dangling
Pointers](https://www.ndss-symposium.org/wp-content/uploads/2017/09/03_4_2.pdf)
[[note](../notes/mem_safety/safe_impl/2015-FreeSentry-NDSS15.md)]

[EuroSys'17] [DangSan: Scalable Use-after-free
Detection](https://www.cs.vu.nl/~giuffrida/papers/dangsan_eurosys17.pdf)
[[note](../notes/mem_safety/safe_impl/2017-DangSan-EuroSys17.md)]

[PLDI'17] [Simple, Fast and Safe Manual Memory
Management](https://www.microsoft.com/en-us/research/wp-content/uploads/2017/03/kedia2017mem.pdf)

[CCS'17] [FreeGuard: A Faster Secure Heap
Allocator](https://dl.acm.org/doi/10.1145/3133956.3133957)

[CCS'18] [A Robust and Efficient Defense against Use-after-Free Exploits
via Concurrent Pointer
Sweeping](https://www.eecis.udel.edu/~hnw/paper/ccs18.pdf)

[Internetware'18] [DangDone: Eliminating Dangling Pointers via Intermediate
Pointers](https://dl.acm.org/doi/abs/10.1145/3275219.3275231)

[IEEE Access'19] [Mpchecker: Use-After-Free Vulnerabilities Protection Based on
Multi-Level Pointers](https://ieeexplore.ieee.org/document/8675929)

[Oakland'20] [MarkUs: Drop-in use-after-free prevention for low-level
languages](https://www.cl.cam.ac.uk/~tmj32/papers/docs/ainsworth20-sp.pdf)

## Secure Memory Allocator
[PLDI'06] [DieHard: Probabilistic Memory Safety for Unsafe
Languages](https://scholarworks.umass.edu/cgi/viewcontent.cgi?article=1086&context=cs_faculty_pubs)

[ASPLOS'08] [Archipelago: Trading Address Space for Reliability and
Security](https://people.cs.umass.edu/~emery/pubs/asplos147-lvin.pdf)

[CCS'10] [DieHarder: Securing the
Heap](https://people.cs.umass.edu/~emery/pubs/ccs03-novark.pdf)

[Sec'18] [GUARDER: A Tunable Secure
Allocator](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-silvestro.pdf)
