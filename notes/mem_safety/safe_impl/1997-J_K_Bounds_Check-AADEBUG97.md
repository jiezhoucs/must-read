# Title, Author(s), and Venue
[AADEBUG'97] **Backwards-compatible bounds checking for arrays and pointers
in C programs**

Richard W M Jones and Paul H J Kelly

ICL

### Category and Keywords
**memory safety**

### What problem does this paper try to solve?
Detecting out-of-bounds access bugs in C programs.

### Why is the problem important?

### What is this paper's solution to the problem?
It is an object-based approach. For a heap object, it stores its metadata,
mainly base and size, to a metadata table (implemented as a splay tree).
For pointer arithmetic, it checks if the source and destination pointers
are valid by range-based lookups in the metadata table. If the result pointer
is out of bounds, set it to an invalid address value (-2 in the implementation).
For pointer dereferences and many other pointer operations such as pointer
comparison, it checks the validity of the pointer.

To differentiate if an OOB pointer is pointing to the location right after
the end of an array, which is an defined behavior by C's standard, or any
other OOB locations, it pads one extra byte after every object and does
not set a pointer to invalid if it points to the extra byte. In this way,
it distinguishes this special OOB pointer with an pointer that points to
the beginning of another memory object that would have been located right
after the former object. Unfortunately, it cannot pad function parameters
because it would change the parameter layout and thus may break
compatibility between checked and unchecked code.

For stack objects, it adopted C++'s constructor/destructor mechanism.

For static and global variables, it constructed a table for them and
loaded at run-time before the programs stats. Statically allocated objects
are also padded.

### What are the strengths of this paper?
It is backward compatible because it associates object metadata with the
object itself rather than with pointers. So no compatibility issue arises
when a pointer is passed around.

### What are the limitations/weaknesses of this paper?
- It does not support temporary out-of-bounds pointers, which are quite
  common in C programs.
- The execution overhead is too high. The paper reports that most programs
  slow down 5x - 6x. The SoftBound paper reports 7.4x - 12x slowdown on
  SPEC and Olden.
- It cannot detect intra-object OOB accesses.
- There are not accurate evaluation numbers.

### What are other solutions and what are the most relevant works?
Most relevant:
- [CRED](https://www.ndss-symposium.org/wp-content/uploads/2017/09/A-Practical-Dynamic-Buffer-Overflow-Detector-Olatunji-Ruwase.pdf)

### What is the take-away message from this paper?

### Other comments
This paper is quite impactful. It should be the paper that pioneered
the "object-based" approach for dynamic bounds checking.

#### Cast between pointers and integers.
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

#### Too many pointer checking
One reason why the approach is too slow is that it inserts too many checks on
too many kinds of pointer operations besides pointer arithmetic and pointer
dereference. Table 3 of the paper listed all the pointer operations that
would be checked.
