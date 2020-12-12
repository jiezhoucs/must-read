# Title, Author(s), and Venue
[NDSS'19] **CRCount: Pointer Invalidation with Reference Counting to Mitigate
Use-after-free in Legacy C/C++**

Jangseop Shin\*, Donghyun Kwon\*, Jiwon Seo\*, Yeongpil Cho\+, Yunheung Paek\*

\*Seoul National University
\+Soongsil University

### Category and Keywords
**temporal memory safety**, **UAF**, **reference counting**

### What problem does this paper try to solve?

### Why is the problem important?

### What is this paper's solution to the problem?
It is a reference counting solution. The high-level idea of reference counting
is to keep a reference counter for each memory object and only free
an object when its counter reaches 0. The counter is increased when a
new pointer is set to the object and decreased when one of its pointers is
set to point something else.

CRCount's novelty lies in how they manage the reference counter.
To that end, it uses two core auxiliary data structures.
First, it adopted the two-level shadow memory from METAlloc to map each
pointer to its pointee's metadata, including a reference counter.
The second data structure, called *pointer bitmap*, is also a shadow memory
that maps every 8-byte of memory of the whole address space to only one bit
that indicates if the mapped location stores a pointer.
For operations that might invalidate pointers, such as
`memset/memcpy/free/return`, it scans the target memory area and checks the
pointer bitmap to identify all pointers and decrease the corresponding
reference counters. A memory object gets really freed when its reference
counter reaches 0.

### What are the strengths of this paper?

### What are the limitations and weaknesses of this paper?
- Similar to DANGNULL, DangSan, and pSweeper, it only instruments LLVM's
  `StoreInst` and thus it ignores all pointers in SSA registers. As a result,
  a reference counter could be smaller than the real number of pointers
  pointing to an object and thus would leave pointers dangling after an
  object is freed.
- It only does intra-procedural data flow analysis to detect casts between
  a pointer and an integer. So if a pointer is cast to an integer and passed
  to a function call, then it may fail to instrument related store
  instructions in the caller. Similarly, if a pointer is cast and stored in
  an integer in a struct and the struct is passed around the memory, it
  may miss instrumenting stores and thus make a lower reference counter.
- It assumes every pointer is aligned on a 8-byte boundary. This assumption
  is true for most programs but there are also some programs using custom
  memory allocator that aligns pointers to 4-byte boundary.
- There are memory leaks. This could be a deal breaker for long-running
  programs such as servers.
- It cannot support custom memory allocators perfectly. Specifically,
  if a custom memory allocator internally allocates memory from a
  reserved chunk of memory, it would fail to do corresponding point-object
  mapping registration because it only intercepts the standard `malloc`
  and `new` family functions or instructions. CRCount's solution is to identify
  these cases and manually insert its runtime library calls.

### What are other solutions and what are the most relevant works?
- MarkUs @Oakland'20
- FFmalloc @Sec'21

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
- In the introduction this paper talks like it is the first one that invented
  reference counting for C. I think a more fairer way of presenting is clearly
  introducing reference counting as background information and stating how
  it improves upon traditional reference counting for C.
- It reports a geo. mean of 18% memory overhead (maximum RSS) on SPEC 2006,
  which is surprising to me. It uses a two-level shadow memory for
  point-object mapping and the delayed free could also increase memory overhead.
  I don't fully understand why the memory overhead is so low.
