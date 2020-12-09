# Title, Author(s), and Venue
[EuroSys'17] **DangSan: Scalable Use-after-free Detection**

Erik van der Kouwe, Vinod Nigade, and Cristiano Giuffrida
@ Vrije University

### Category and Keywords
**temporary memory safety**, **UAF**

### What problem does this paper try to solve?
Use-After-Free memory safety bugs.

### Why is the problem important?

### What is this paper's solution to the problem?
Similar to previous related work DANGNULL and FreeSentry, DangSan also
uses complex data structures to keep track of the point-to relations of a
program and invalidate dangling pointer at memory deallocation.

DangSan consists of four major components.

**pointer tracker**: it finds stores of pointers and calls a function
`registerptr()` to register it. `registerptr` queries the **pointer-to-object
mapper** to get the pointed object and then registers the pointer's location
and the object to the **pointer logger**.

**heap tracker**: it intercepts `malloc` and `free` to initialize the
pointer-to-object mapping and invalidate all dangling pointers.
At memory allocation, it creates metadata (mainly its starting address and size)
for the object, and register the metadata and the initial pointer to
the object to the **pointer-to-object mapper**.
At memory deallocation, it queries the **pointer-to-object mapper** to
locate the corresponding object and passes it to the **pointer logger** to
invalidate all dangling pointers.

**pointer-to-object mapper**: it maps a pointer to the metadata of the
pointer object. It's implemented as a two-level shadow memory, adopted
from the METAlloc paper.

**pointer logger**: it keeps track of all the pointers to their pointee on
a per-thread view. Whenever a pointer is updated (excluding certain cases
such as simple pointer arithmetic on the same pointer), it is registered in
the logger. When an object is freed, a function `invalptrs()` walks through the
log invalidates all valid pointers. It invalidates a pointer by setting
the most significant bit to 1.
It is inspired by *log-structured file systems*, and it is lock-free.

The performance overhead on SPEC06 is 41%.

### What are the strengths of this paper?
- It works for multi-threading programs.

### What are the limitations and weaknesses of this paper?
- Temporary OOB pointers might cause trouble. If a pointer is temporarily
  out-of-bounds and thus points to another object which is later freed before
  the temporary OOB pointer comes back within bounds, the pointer would get
  invalidated. Then when the pointer is "restored", dereferencing to it
  would cause error. This kind of pointers are common in certain programs.
  Table 1 of the CHERI ASPLOS15 paper shows that `tcpdump` from SPEC06 has
  1,299 such *invalid intermediate* pointers.
- It suffers a common problem shared by all dangling-pointer-invalidation
  approaches: non-dereference use, such as pointer arithmetic or being used
  as a key for hash table query, of dangling pointers. Although it is undefined
  behavior by C's standard, it is very rare.
- Another common problem: it does not track pointers copied in a type-unsafe
  way such as pointers being cast to integers and pointers copied by `memcpy()`.
- It does not track pointers in registers and pointers spilled onto the stack
  at function prologue. Similarly, DANGNULL and FreeSentry share this
  limitation.
- There is a race condition at free: if a to-be-invalidated pointer is
  propagated by another thread to a register and the register is copied back
  to memory, this dangling pointer would survive the invalidation process.
  The pSweeper paper also discusses dangling pointer propagation (Section 4.5).
- If an integer is stored at the location where a pointer was stored and
  the integer happens to have the same value as the pointer, DangSan might
  accidentally invalidate this integer when it frees the object used to be
  pointed by that pointer. But the papers argues this should be
  a very rare case.
- The memory overhead is too high: 2.4x on SEPC06. For Apache, the memory
  overhead is 4.5x (40MB to 179MB); for Nginx, it is 1.8x (20MB to 36MB).

### What are other solutions and what are the most relevant works?
- METAlloc @EuroSec16
- DANGNULl @NDSS15
- FreeSentry @NDSS15

#### Related links

### Thing(s) that I like particularly about this paper.
- Drawing ideas from "old" research ideas is good.

### What is the take-away message from this paper?

### Other comments
- It uses a two-level shadow memory for pointer-to-object metadata mapping.
  One needs to read the METAlloc paper first to understand this data structure.
- Both this paper and the FreeSentry paper mentions the case that the object
  that contains the to-be-invalidated pointer has already been freed and the
  memory for the object was reclaimed by the OS. In this case, there would be
  a segfault. FreeSentry keeps a bit-array that indicates the liveness of
  each page and checks a page's liveness before invalidating a pointer.
  DangSan catches the `SEGSEGV` signal and skip the pointer invalidation.
