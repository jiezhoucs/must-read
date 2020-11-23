# Title, Author(s), and venue.
[NDSS'15] **Preventing Use-after-free with Dangling Pointers Nullification**

Byoungyoung Lee, Chengyu Song, Yeongjin Jang, Tielei Wang, Taesoo Kim, Long
Lu,\* Wenke Lee

Georgia Tech

\*Stony Brook University

### Category and Keywords
memory safety; dangling pointers; Use-after-Free (UaF);

### What problem does this paper try to solve?
Use-after-Free and Double Free vulnerabilities caused by dangling pointers in
programs written in C and C++.

### Why is the problem important?
Vulnerabilities induced by these errors can lead to disastrous consequences:
information leaking, data corruption, or even a whole system being hijacked.

### What is this paper's solution to the problem?
It tracks the point-to relations for heap objects in the target program,
and at memory deallocation, it invalidates all the pointers to the freed object.

It uses a `red-black tree` (called `ShadowObjTree`) to track the point-to
relations. Each node of the tree represents a live memory object. It holds the
memory layout information about the object and it contains information about
which pointers are pointing to this object (in-bound pointers) and which of its
pointers (out-bound pointers) is pointing to which other heap object.  Each node
has two sub-trees for the in/out-bound pointers; they are also implemented as
`red-black trees`. At memory allocation, it inserts a new node to the
`ShadowObjTree`. At pointer propagation, it adds a function call to update
the tree by updating both the in-bound and out-bound trees for the corresponding
objects. At pointer deallocation, it gets all the in-bound pointers to the
freed object and invalidate them; and it also removes these in-bound pointers
from the out-bound trees of the objects that hold the in-bound pointers.
Besides, it removes all its out-bound pointers from the in-bound tree of
the objects to which these out-bound pointers point.

### What are the strengths of this paper?
- The algorithm of instrumenting the code is relatively straightforward
  and easy to follow.
- The evaluation is strong: it evaluates DANGNULL on SPEC2006 and Chromium, and
  it breaks down their implementation to see how much impact each component
  brings.

### What are the limitations of this paper?
- It only track pointers residing on the heap to heap objects. Eliding tracking
  stack objects is acceptable, but it is questionable to ignore stack pointers
  to heap objects. The paper argues that stack pointers usually live short
  so it is difficulty to exploit stack dangling pointers. It makes sense
  intuitively but lacks convincing scientific evidence.
- Both the performance overhead and memory overhead are high for
  pointer-intensive programs. The performance average overhead is 80% on SPEC
  with the highest more than 400%. The highest memory overhead is over 10x
  Note that this the overhead from only tracking pointers living on the heap.
  As result, they did not track any pointers for 9 out of 16 SPEC benchmarks
  (Table V).
- It could raise false positives when a dangling pointer is used in a
  non-dereference way, such as pointer arithmetic or key for a hash-table
  search.
- It does not trace pointer cast to integers. This is a limitation shared by
  almost all the related work.

### What are other solutions and what are the most relevant works?
- FreeSentry @NDSS'15
- DangSan @EuroSys'17
- pSweeper @CCS'18

### Thing(s) that I like particularly about this paper.
It used Chromium to test their implementation.

### What is the take-away message from this paper?

### Other comments and notes
#### Questions
- In Algorithm 2, what does line 14 do exactly?
- In Algorithm 2, what exactly is the `ptr` made of at line 15?
- In Algorithm 2, why is line 26 needed?

#### others
- It's not clear how they measured the memory overhead.
- It presents tons of experimental data, but some of them are not clearly
  explained. For example, in Table V, it didn't detect any heap pointers
  for many programs, but some of those programs, e.g., `hmmmer` still has
  high memory overhead. Without pointer tracking, the only memory overhead
  should come from the red-black tree tracking the legal bounds of each
  heap object. Intuitively the overhead shouldn't be that high.
