# Title, Author(s), and Venue
[NDSS'15] **FreeSentry: Protecting Against Use-After-Free Vulnerabilities Due to
Dangling Pointers**

Yves Younan

Talos Security Intelligence and Research Group Cisco Systems

### Category and Keywords
**temporal memory safety**, **use-after-free**

### What problem does this paper try to solve?

### Why is the problem important?

### What is this paper's solution to the problem?
It tracks the point-to relations of a program and nullifies the dangling
pointers when a memory object is freed.

Supporting data structures: (illustrated in Figure 2)
- *pointer registration information* (PRI): it contains a pointer's address,
  the label of the pointed object, pointers to the previous and next PRI entry
  for the same object, and pointers to the previous and next PRI entry for
  a different object due to hash collision.
- *label lookup table*: each memory object is companied with a piece of shadow
  memory and a label for the object is stored in each shadow memory slot for
  the object. The label is used as the index to locate the target item in the
  object lookup table.
- *object lookup table*: it contains the pointers to PRIs.  An item is located
  based on the address of an object. In the implementation, an item is indexed
  by a label in the label lookup table.
- *pointer lookup table*: a hash table that maps a pointer right-shifted by
  4 bits to the address of the pointer's PRI item.

At memory allocation, the label lookup table is updated; the address of the
pointer to the new object is registered in both the object lookup table and
the pointer lookup table; the pointer and related information is registered
in the PRI.
When a pointer is updated, it is looked up via the pointer lookup table
and the corresponding entry in the PRI is updated.

At memory deallocation, it queries the object lookup table and find related
entries in the PRI. The pointers in these entries are then invalidated and
the entries are removed from the PRI.

For stack protection, it calls a functions to label the current stack frame
when a function starts and invalidates pointers to the current stack when
a function exits.  For each `alloca()` call, it makes the call to allocate
a multiple of the predefined minimum object size (for easy shadow
memory purpose) and adds more labels in the label lookup table.
For `setjmp/longjmp`, it intercepts calls to `longjmp()` and unwinds
the stack frames to invalidate all the pointers on those stacks.

To allow pointer arithmetic on pointers after they are invalidated,
it invalidates a dangling pointer by setting the fist two bits to 1, instead
of setting the whole pointer to 0.

### What are the strengths of this paper?

### What are the limitations and weaknesses of this paper?
- The prototype only works for C but not C++.
- It does not track pointers cast integers. Again, this is a limitation shared
  by most related works.
- It did not measure memory overhead. Based on all the data structures it
  uses and the minimum object size (32 byte) for easy shadow memory,
  the memory overhead should be very high. I bet the geo. mean on SPEC06
  would be at least 3x.

### What are other solutions and what are the most relevant works?
Mostly related:
- DangNull @NDSS15
- DanSan   @EurySys17

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
- This paper was really terribly written - unclear in describing the mechanism;
  and the typesetting is ugly.
