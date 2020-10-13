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
It stores the metadata, mainly base and limit, and maybe additional information
to improve error reporting, of a memory object in a splay tree. For
pointer reference, it checks if the pointer falls in a valid range of
a memory object.  For pointer arithmetics, if the arithmetic result
is out of bound, it sets the pointer to be -2.

### What are the strengths of this paper?
It is backward compatible because it associates object metadata with the
object itself rather than with pointers. So no compatibility issue arises
when a pointer is passed around.

### What are the limitations/weaknesses of this paper?
- It does not support intermediate out-of-bounds pointers, which are quite
  common in C programs.
- The execution overhead is too high. The paper reports that most programs
  slow down 5x - 6x. The SoftBound paper reports 7.4 - 12 slow down on
  SPEC and Olden.
- It cannot detect out-of-bound access to arrays inside a struct.
- Pointers returned from an unchecked function might be illegal.
- There are not accurate evaluation numbers.

### What are other solutions and what are the most relevant works?
Most relevant:
[CRED](https://www.ndss-symposium.org/wp-content/uploads/2017/09/A-Practical-Dynamic-Buffer-Overflow-Detector-Olatunji-Ruwase.pdf)

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
It's not clear to me how this paper handles cast between pointers and
integers. For example, if a pointer is cast to an integer, and the
integer gets incremented to out of the bound of the intended referent
of the pointer, and then the integer gets cast back to a pointer and it
points to another valid memory object, would this situation be detected?

10/08/2020 Update: I'm almost sure this type of errors would not be caught.
Catching such errors requires to track certain integers, and the paper
does no talk about how to do it. Besides, at the last paragraph of the
Future section of the paper says,

> The most serious in practice is that it is possible to manufacture
> erroneous pointers using unions, casts and unitialised data.
> At considerable performance cost, we could maintain a shadow of the
> accessible store, indicating whether it has been initialised and whether
> it is a pointer.
