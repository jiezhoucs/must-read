# Title, Author(s), and Venue
[ACSAC'20] **HeapExpo: Pinpointing Promoted Pointers to Prevent Use-After-Free
Vulnerabilities**

Zekun Shen and Brendan Dolan-Gavitt @NYU

### Category and Keywords

### What problem does this paper try to solve?
There is one common limitation in a few previous works DANGNULL,
DangSan, and pSweeper: they only track pointers set by a `StoreInst` but
do not track pointers in LLVM IR virtual registers. Therefore, they would
miss some dangling pointers that only live in registers or spilled to and
loaded from registers.
This is not a small limitation as shown by HeapExpo: these works failed to
detect 10 out of the 19 real-world UAF bugs from the OSS-Fuzz database
due to it.

The FreeSentry paper does not have enough implementation details about
this issue and it is implemented with CIL rather than LLVM. DangSan and
this HeapExpo both believe it shares this same limitation.

### Why is the problem important?

### What is this paper's solution to the problem?
HeapExpo is built upon DangSan. It adds a new pass before LLVM's mem2reg pass
(a pass that promotes operands in memory instructions to virtual registers)
to mark pointers that might be promoted to registers as volatile so that
later optimization passes will keep them in memory. It also adds optimization
passes to omit instrumenting certain pointers if the compiler is sure they
will not become dangling.

On the same benchmarks ran by both DangSan, HeapExpo's performance overhead
is 66%, improving 20% over DangSan. The memory overhead is 100% compared to
DangSan's 87%.

### What are the strengths of this paper?
It showed that the number of missed dangling pointers in registers is much
higher than previous works expected.

### What are the limitations and weaknesses of this paper?
- Its prototype failed running 3 SPEC benchmarks. The papers says they believe
  this is due to bugs in the benchmarks. I guess it's more likely it's caused
  by their own bugs in the implementation.
- Their optimization is based on the assumption that a memory object would only
  be freed by the same thread. Violation of this assumption could cause missing
  dangling pointers. DangSan also has this assumption.
- Another common limitation is it does not handle type-unsafe copies of
  pointers.

### What are other solutions and what are the most relevant works?
- DANGNULL
- FreeSentry
- DangSan
- pSweeper

#### Related links

### Thing(s) that I like particularly about this paper.
It answered an important question that how serious one limitation of previous
works could be. This kind of evaluation is important in systems security.

### What is the take-away message from this paper?

### Other comments
There are several errors in the paper:
- In the **Address-based checking** paragraph of Section 2.2, it’s not accurate
  to put citation 4 and 19 together with 20 and 25 and it’s not correct to say
  "This type of temporal safety approach tries to invalidate the memory
  addresses of a heap object when it is released.”
  because [4] (Safe-C) and [19] (CETS) use a key-lock (capability) system for
  dynamic checking and they only invalidate the lock (capability) rather than
  the real contents of a memory object when it’s free.
- Section 2.4.1 says DangSan uses a three-level shadow memory to track pointer
  and their metadata.  It's more accurate to say it uses a 2-level shadow memory
  (as the Figure 5 of the DangSan paper shows) because the third level is not a
  shadow memory but the real metadata (pointer logs, etc.). The DangSan paper
  says "We use two levels of shadow memory and, as a consequence, metadata
  lookups require two memory reads.” in the last paragraph of Section 4.3.
- The related work section says FreeSentry used LLVM while actually FreeSentry
  did not use LLVM but CIL.
- Citation [13] should be pSweeper.
- The Related Work section says "In terms of overhead, DangSan is currently the
  state of the art.". It's not true. pSweeper is faster, at the cost of
  extra CPU resources.

Also, in the **Address-based checking** paragraph of the Related Work section,
it says
> However, source- level instrumentation can reduce the opportunities the
> compiler has to optimize the program

I don't think this is true.
