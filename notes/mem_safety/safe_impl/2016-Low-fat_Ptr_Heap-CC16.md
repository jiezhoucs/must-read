# Heap Bounds Protection with Low Fat Pointers
[CC'16]

Gregory J. Duck and Roland H. C. Yap

National University of Singapore


### Category and Keywords
**memory safety**, **low-fat pointer**

### What problem does this paper try to solve?

### Why is the problem important?

### What is this paper's solution to the problem?
The paper designed a new encoding scheme for pointer/object metadata.
An pointer is still 64-bit long and contains a valid memory address to
the referent. The key idea is to change the default memory allocator
to achieve a desired memory layout so that a pointer's address *implicitly*
contains metadata about the referent.

The low-fat allocator divides the heap evenly into M sub-heaps. Each sub-heap
is 4GB in the paper's implementation, but the number can be configured.
Every sub-heap's starting address is a multiple of 4GB, and every sub-heap
is dedicated for memory objects of the same size from a series of
sizes: <16B, 32B, 48B, 64B, ..., 8KB, 16KB, 32KB, ..., 1GB>.
At memory allocation, each object is put to its corresponding sub-heap and
aligned by its size. For example, a memory object of 50 Bytes will be
put to the sub-heap where all memory objects are 64 bytes and this object
is aligned by 64 bytes. In this way, it is easy to compute the base and
the size (not accurate) of a memory object.  For example, pointer
`p = 0x180000000`'s pointee resides in sub-heap 1 (`p >> 32`) and thus
its size is 16 bytes. For non-heap objects and large objects (greater than
the supported largest size), the allocation falls back to use the default
`malloc`; and for all those memory objects, it treats is base as
0 and size as `UINT64_MAX` so the bounds check will always pass.

At allocation, it instruments the returned pointer with a base and a size
(adding extra variables). When a new pointer created by deriving from another
pointer, it propagates the origin pointer's metadata. At pointer dereference,
it inserts a dynamic bounds check. It also inserts bounds check for pointer
arithmetic for several cases (Sec. 4.2.2) such as before passing to a call.

### What are the strengths of this paper?
- It maintains full binary compatibility.

### What are the limitations and weaknesses of this paper?
- It only works on 64-bit architectures.
- It only works for heap memory objects.
- The solution only tracks the allocation bounds rather than the accurate
  object bounds. It is harmless to have write overflow within the allocation
  bounds but may cause trouble with read overflow. This problem can be
  alleviated by using more sizes, but it can not scale to arbitrary
  number of sizes.
- It cannot detect sub-object out-of-bounds (OOB) accesses.
- (Not unique to this paper) The instrumentation on temporary OOB pointers
  may break a program. Between certain pointer arithmetic and
  use (not dereference) of the result pointer, it inserts dynamic check
  on the result pointer. It says if only inserts such check when pointers
  are passed between contexts (function call & return). However, since it
  should be very rare that passing a deliberate-OOB pointer between contexts,
  this limitation may not cause much trouble (breaking "good" program)
  in practice.
- It may break programs that crate temporary OOB pointers.

### What are other solutions and what are the most relevant works?
- [Mid-fat pointer](https://www.cs.vu.nl/~giuffrida/papers/midfat_eurosec17.pdf)

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
I think the term "low-fat pointer" in this paper is a little confusing.
By just looking at the name, I thought it means changing the representation
of a raw C with extra metadata. This paper does encode some metadata (which
memory region the referent is in) in the pointer, but it does so *implicitly*
by changing how memory allocation is managed.
A raw pointer still holds a valid memory address.
