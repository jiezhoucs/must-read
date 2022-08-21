# Safe C/C++ Implementations

[USENIX-Winter'92] [Purify: Fast Detection of Memory Leaks and Access
Errors](https://pdfs.semanticscholar.org/b2c4/44e8ab6b9bea1072bb0a7dd321543c8520ea.pdf)

[PLDI'94] [Efficient Detection of All Pointer and Array Access
Errors](https://web.eecs.umich.edu/~taustin/papers/PLDI94-safec.pdf)

[SPE'97] [Low-cost, Concurrent Checking of Pointer and Array Accesses in C
Programs](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.17.267&rep=rep1&type=pdf)

[AADEBUG'97] [Backwards-compatible bounds checking for arrays and pointers in C
programs](https://www.doc.ic.ac.uk/~phjk/Publications/BoundsCheckingForC.pdf)
[[note](../notes/mem_safety/safe_impl/1997-J_K_Bounds_Check-AADEBUG97.md)]

[FSE'03] [Protecting C Programs from Attacks via Invalid Pointer
Dereferences](http://groups.csail.mit.edu/pag/data/OLD/reading-group/yong03protecting.ps)

[FSE'04] [An Efficient and Backwards-Compatible Transformation to Ensure Memory
Safety of C Programs](http://www.sis.pitt.edu/jjoshi/courses/IS2620/Spring09/Xu.pdf)

[NDSS'04] [A Practical Dynamic Buffer Overflow
Detector](https://suif.stanford.edu/papers/tunji04.pdf)
[[notes](../notes/mem_safety/safe_impl/2004-CRED-NDSS04.md)]

[SPACE'04] [Bounds-Checking Entire Programs without
Recompiling](http://forskning.diku.dk/topps/space2004/space_final/nethercote-fitzhardinge.pdf)

[ACSAC'04] [A Dynamic Technique for Eliminating Buffer Overflow Vulnerabilities
(and Other Memory Errors)](https://www.acsac.org/2004/papers/98.pdf)

[TECS'05] [Memory Safety Without Garbage Collection for Embedded
Applications](https://llvm.org/pubs/2005-02-TECS-SAFECode.pdf)

[ICSE'06] [Backwards-Compatible Array Bounds Checking for C with Very Low
Overhead](http://llvm.org/pubs/2006-05-24-SAFECode-BoundsCheck.pdf)

[PLDI'06] [SAFECode: Enforcing Alias Analysis for Weakly Typed
Languages](http://llvm.org/pubs/2006-05-12-PLDI-SAFECode.pdf)

[PLDI'09] [Implementation of the Memory-safe Full ANSI-C
Compiler](https://dl.acm.org/doi/10.1145/1542476.1542505)

[PLDI'09] [SoftBound: Highly Compatible and Complete Spatial Memory Safety for
C](http://www.cis.upenn.edu/acg/papers/pldi09_softbound.pdf)

[AsiaCCS'10] [PAriCheck: An Efficient Pointer Arithmetic Checker for C
Programs](http://fort-knox.org/files/paricheck.pdf)

[CGO'11] [Practical Memory Checking with Dr. Memory](https://dl.acm.org/doi/10.5555/2190025.2190067)

[CGO'12] [Light-weight Bounds Checking](http://seclab.cs.sunysb.edu/seclab/pubs/lbc.pdf)

[ATC'12] [AddressSanitizer: A Fast Address Sanity
Checker](https://www.usenix.org/system/files/conference/atc12/atc12-final39.pdf)
[[notes](../notes/mem_safety/safe_impl/2012-ASan-ATC12.md)]

[SPE'13] [MemSafe: Ensuring the Spatial and Temporal Memory Safety of C at
Runtime](https://onlinelibrary.wiley.com/doi/epdf/10.1002/spe.2105)

[ISSRE'14] [WPBOUND: Enforcing Spatial Memory Safety Efficiently at Runtime
with Weakest Preconditions](http://www.cse.unsw.edu.au/~jingling/papers/issre14.pdf)

[PLAS'15] [Memory-safe Execution of C on a Java VM](https://chrisseaton.com/plas15/safec.pdf)

[SNAPL'15] [Everything You Want to Know About Pointer-Based
Checking](https://core.ac.uk/download/pdf/62919692.pdf)

[EuroSec'16] [METAlloc: Efficient and Comprehensive Metadata Management
for Software Security Hardening](https://www.cs.vu.nl/~giuffrida/papers/eurosec-2016.pdf)

[CC'16] [Heap Bounds Protection with Low Fat
Pointers](https://www.comp.nus.edu.sg/~gregory/papers/cc16lowfatptrs.pdf)
[[note](../notes/mem_safety/safe_impl/2016-Low-fat_Ptr_Heap-CC16.md)]

[NDSS'17] [SafeInit: Comprehensive and Practical Mitigation of Uninitialized
Read Vulnerabilities](https://download.vusec.net/papers/safeinit_ndss17.pdf)

[EuroSec'17] [Fast and Generic Metadata Management with Mid-Fat
Pointers](https://www.cs.vu.nl/~giuffrida/papers/midfat_eurosec17.pdf)

[AsiaCCS'17] [DataShield: Configurable Data Confidentiality and
Integrity](https://nebelwelt.net/publications/files/17AsiaCCS.pdf)

[CCS'17] [HexType: Eicient Detection of Type Confusion Errors for
C++](https://lifeasageek.github.io/papers/jeon-hextype.pdf)

[PLDI'18] [EffectiveSan: Type and Memory Error Detection using Dynamically
Typed C/C++](https://dl.acm.org/doi/10.1145/3296979.3192388)

[AsiaCCS'18] [CUP: Comprehensive User-Space Protection for
C/C++](https://nebelwelt.net/files/18AsiaCCS.pdf)
[[note](../notes/mem_safety/safe_impl/2018-CUP-AsiaCCS18.md)]

## Temporal
### Secure Allocation
[DSN'06] [Efficiently Detecting All Dangling Pointer Uses in Production
Servers](https://llvm.org/pubs/2006-DSN-DanglingPointers.pdf)
[[note](../notes/mem_safety/2006-D_A_UAF-DSN06.md)]

[PLDI'07][Exterminator: Automatically Correcting Memory Errors with High
Probability](https://people.cs.umass.edu/~emery/pubs/pldi028-novark.pdf)

[Sec'10] [Cling: A Memory Allocator to Mitigate Dangling
Pointers](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.172.8557&rep=rep1&type=pdf)

[NDSS'19] [CRCount: Pointer Invalidation with Reference Counting to Mitigate
Use-after-free in Legacy C/C++](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_05A-4_Shin_paper.pdf)
[[note](../notes/mem_safety/safe_impl/2019-CRCount-NDSS19.md)]

### Key-lock Checking
[ISMM'10] [CETS: Compiler-Enforced Temporal Safety for
C](http://www.cis.upenn.edu/acg/papers/ismm10_cets.pdf)

[ISSTA'21] [UAFSan: An Object-Identifier-Based Dynamic Approach for Detecting
Use-After-Free Vulnerabilities](https://dl.acm.org/doi/abs/10.1145/3460319.3464835)

### Dangling Pointer Invalidation
[NDSS'15] [Preventing Use-after-free with Dangling Pointers
Nullification](https://wenke.gtisc.gatech.edu/papers/dangnull.pdf)
[[note](../notes/mem_safety/safe_impl/2015-DANGNULL-NDSS15.md)]

[NDSS'15] [FreeSentry: Protecting Against Use-After-Free Vulnerabilities Due to
Dangling Pointers](https://www.ndss-symposium.org/wp-content/uploads/2017/09/03_4_2.pdf)
[[note](../notes/mem_safety/safe_impl/2015-FreeSentry-NDSS15.md)]

[EuroSys'17] [DangSan: Scalable Use-after-free
Detection](https://www.cs.vu.nl/~giuffrida/papers/dangsan_eurosys17.pdf)
[[note](../notes/mem_safety/safe_impl/2017-DangSan-EuroSys17.md)]

[CCS'18] [A Robust and Efficient Defense against Use-after-Free Exploits
via Concurrent Pointer Sweeping](https://www.eecis.udel.edu/~hnw/paper/ccs18.pdf)
[[note](../notes/mem_safety/safe_impl/2018-pSweeper-CCS18.md)]

[Internetware'18] [DangDone: Eliminating Dangling Pointers via Intermediate
Pointers](https://dl.acm.org/doi/abs/10.1145/3275219.3275231)

[IEEE Access'19] [Mpchecker: Use-After-Free Vulnerabilities Protection Based on
Multi-Level Pointers](https://ieeexplore.ieee.org/document/8675929)

[ACSAC'20] [HeapExpo: Pinpointing Promoted Pointers to Prevent Use-After-Free
Vulnerabilities](http://moyix.net/~moyix/papers/heapexpo.pdf)
[[note](../notes/mem_safety/safe_impl/2020-HeapExpo-ACSAC20.md)]

## Secure Memory Allocator
[PLDI'06] [DieHard: Probabilistic Memory Safety for Unsafe
Languages](https://scholarworks.umass.edu/cgi/viewcontent.cgi?article=1086&context=cs_faculty_pubs)

[EuroSys'08] [Samurai: Protecting Critical Data in Unsafe
Languages] [paper](http://blogs.ubc.ca/karthik/files/2009/11/Eurosys-camera-ready.pdf)
[related slides](https://www.microsoft.com/en-us/research/uploads/prod/2017/01/ndure-overview-12-06.pdf)

[ASPLOS'08] [Archipelago: Trading Address Space for Reliability and
Security](https://people.cs.umass.edu/~emery/pubs/asplos147-lvin.pdf)

[CCS'10] [DieHarder: Securing the Heap](https://people.cs.umass.edu/~emery/pubs/ccs03-novark.pdf)

[CCS'17] [FreeGuard: A Faster Secure Heap
Allocator](https://dl.acm.org/doi/10.1145/3133956.3133957)

[Sec'18] [GUARDER: A Tunable Secure Allocator](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-silvestro.pdf)

[Oakland'20] [MarkUs: Drop-in use-after-free prevention for low-level
languages](https://www.cl.cam.ac.uk/~tmj32/papers/docs/ainsworth20-sp.pdf)

[ARES'21] [MESH: A Memory-Efficient Safe Heap for C/C++](https://dl.acm.org/doi/pdf/10.1145/3465481.3465760)
