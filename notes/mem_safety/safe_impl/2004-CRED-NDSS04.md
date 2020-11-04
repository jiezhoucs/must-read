# Title, Author(s), and Venue
[NDSS'04] **A Practical Dynamic Buffer Overflow Detector**

Olatunji Ruwase of Transmeta Corporation and
Monica S. Lam of Stanford

### Category and Keywords
**memory safety**

### What problem does this paper try to solve?
The Jones and Kelly's bounds checking method has a severe limitation:
it does not allow temporary OOB pointers. Unfortunately temporary OOB
pointers are common in C programs and thus J&K's would break many
normal C programs. This paper builds on J&K's and solved this problem.

### What is this paper's solution to the problem?
CRED creates an OOB object for each OOB pointer, and it replaces the
value of the OOB pointer with the address of the OOB object. The OOB object
contains the OOB pointer and "the referent object that the value refers to".
(The paper is not very clear on what exactly about the referent is(are) stored
in an OOB. I assume it is the start address, perhaps plus the size about the
referent.) The address of each live OOB object is stored in an OOB hash table.

At pointer arithmetic, it first checks if the pointer points to an object
in the object table or points to an unchecked object. If neither is the case,
if checks the OOB hash table and performs the computation on the OOB pointer
if one entry is found. (See more about this in the comments.)
This enables recovering a temporary OOB pointer back to a valid pointer.

### What are the strengths of this paper?

### What are the limitations and weaknesses of this paper?
- It only checks pointers to strings.
- It allows passing OOB object pointers (the address of the the OOB object, not
  the OOB pointer itself) to unchecked code; so it would cause
  undefined behavior if an OOB pointer is dereferenced in the unchecked code.
- Like many other approaches, it cannot handle the case where a pointer
  is cast to an integer and cast back. The "recovered" pointer may
  point to another valid object without being detected.
- I don't think this paper was clearly-written.

### What are other solutions and what are the most relevant works?
- [Jones & Kelly's](https://www.doc.ic.ac.uk/~phjk/Publications/BoundsCheckingForC.pdf)

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments

> All problems in computer science can be solved by another level of
> indirection.  --David Wheeler

#### Confusing text.
The paper is not clear about how to determine if an object is an unchecked
object. The J&K's paper discusses the situation where a pointer cannot be
located in the object table. The pointer could be an OOB pointer, or could
point to an unchecked objects that are created by unchecked code. In both
cases the program can continue executing. In the CRED paper, it is not clear
how to determine if a pointer is an OOB pointer or it points to an unchecked
object. This should be easy to determine by simply checking the OOB hash table.
However, in the third step of the technique described in Section 2.2,
the paper says:

> If a pointer is used in an arithmetic or comparison operation, checks if it
points to an object or to an unchecked object. If neither is the case,
check the OOB hash table to determine if it is an out-of-bounds value.

This seems to imply that checking if a pointer points to an unchecked object
is a separate step before the OOB hash table lookup is performed.
This is confusing.

Besides, the paper does not say what to do if no entry is found in the
OOB tabel; based on my understanding of the J&K's paper, in this case
it assumes the point points to an unchecked object and continues executing.
