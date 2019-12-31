# Title, Author(s), and Venue
**Backwards-compatible bounds checking for arrays and pointers in C programs**

Richard W M Jones and Paul H J Kelly

[AADEBUG'97]

### Category and Keywords
**memory safety**

### What problem does this paper try to solve?
Detecting out-of-bounds access bugs in C programs.

### Why is the problem important?

### What is this paper's solution to the problem?
It stores the metadata (mainly base and limit, and maybe additional information
to improve error reporting) of a memory object in a splay tree. For
pointer reference, it checks if the pointer falls in a valid range of
a memory object.  For pointer arithmetics, it updates the pointer metadata;
if the arithmetic result is out of bound, it sets the pointer to be -2.

### What are the strengths of this paper?
It is backward compatible because it associates object metadata with the
object itself rather than with pointers. So no compatibility issue arises
when a pointer is passed around.

### What are the limitations of this paper?
- It does not support intermediate out-of-bounds pointers, which are quite
common in C programs.
- The execution overhead is too high. The paper reports that most programs
  slow down 5x - 6x. The SoftBound paper reports 7.4 - 12 slow down on
  SPEC and Olden.
- It cannot detect out-of-bound access to arrays inside a struct.

### What are other solutions and what are the most relevant works?

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
