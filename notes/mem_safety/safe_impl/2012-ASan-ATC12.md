# Title, Author(s), and Venue
[ATC'12] **AddressSanitizer: A Fast Address Sanity Checker**

Konstantin Serebryany, Derek Bruening, Alexander Potapenko, Dmitry Vyukov

Google

### Category and Keywords
**memory safety**, **shadow memory**

### What problem does this paper try to solve?
Detecting memory safety errors, mainly buffer overflows and use-after-free.

### Why is the problem important?

### What is this paper's solution to the problem?
The core idea is to use shadow memory to monitor the liveness of the regular
memory regions.

**mapping**: By default ASan maps every 8 bytes of regular memory to
one byte of shadow memory.

**encoding**: The content in each one-byte shadow memory could be
- 0: meaning all the corresponding 8 bytes of memory are valid
- 1 to k (1 <= k <= 7): the first k bytes are valid
- negative value: the entire 8-byte memory is invalid. Different negative values
  are used to differentiate kinds of unaddressable memory (heap redzones,
  stack redzones, global redzones, freed memory).

Redzones are placed between valid memory regions. Redzones serve two purposes.
First, they can be used to detect consecutive buffer overflows.
Second, they contains metadata, e.g. object size, thread ID,
about the allocated memory.

**spatial memory safety**: consecutive buffer overflow and underflow
(both read and write) can be detected because redzones are placed on both
sides of a valid memory region and the shadow memory for redzones are set
to be unaddressable.

**temporal memory safety**: After a memory region is freed, its shadow memory
counterpart is set to be unaddressable. ASan delays reusing just freed memory
regions by putting them into quarantine.

### What are the strengths of this paper?
- The high-level idea is simple.

### What are the limitations of this paper?
**spatial memory safety**:
- It cannot detect all arbitrary memory access errors.
  A memory read or write may stride across redzone(s) and land onto another
  valid object.
- A rare case is when an unaligned access is partially out-of-bounds.
  For example, an object is 8 bytes longs; if a 4-byte read/write starts from
  the 7th byte, then there would be 2 bytes of memory over-read/written without
  being detected by ASan.

**temporal memory safety**: A dangling pointer can access a reallocated memory
region after it is released from the quarantine space.

### What are other solutions and what are the most relevant works?

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
