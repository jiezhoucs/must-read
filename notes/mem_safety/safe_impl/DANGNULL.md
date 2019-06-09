# Title, Author(s), and venue.
**Preventing Use-after-free with Dangling Pointers Nullification**

Byoungyoung Lee, Chengyu Song, Yeongjin Jang, Tielei Wang, Taesoo Kim, Long Lu,
Wenke Lee

NDSS'15

### Category and Keywords
memory safety; dangling pointers; Use-after-Free (UaF); 

### What problem does this paper try to solve?
Use-after-Free and Double Free vulnerabilities caused by dangling pointers in
programs written in C and C++.

### Why is the problem important?
Vulnerabilities induced by these errors can lead to disastrous consequences:
information leaking, data corruption, or even a whole system being hijacked.

### What is this paper's solution to the problem?
It instruments the code to trace all pointers created by memory allocators to
heap objects and the point-to relations between those pointers. For every memory
deallocation event, it sets all the pointers pointing to the deallocated object
to invalid. 

### What are the strengths of this paper?
- The algorithm of instrumenting the code is relatively straightforward and easy
  to follow.
- The evaluation is strong: it evaluates DANGNULL on SPEC2006 and Chromium, and
  it breaks down their implementation to see how much impact each component
  brings.

### What are the limitations of this paper?
- Not-low performance overhead: average overhead of 80% on SPEC (1% to 472%).
- Requires source code.

### What are other solutions and what are the most relevant works?

### Thing(s) that I like particularly about this paper.
It used Chromium to test their implementation. And they looks as honest as the 
RocSec group.

### What is the take-away message from this paper?
