# Title, Author(s), and Venue
[CCS'18] **A Robust and Efficient Defense against Use-after-Free Exploits via
Concurrent Pointer Sweeping**

Daiping Liu and Haining Wang @ UofDelaware and Mingwei Zhang @Intel Labs

### Category and Keywords
**memory safety**, **temporal memory safety**, **UAF**

### What problem does this paper try to solve?

### Why is the problem important?

### What is this paper's solution to the problem?
Similar to DANGNULL, FreeSentry, and DangSan, it invalidates dangling pointers,
but it improves the performance greatly with two key differences.
First, it only tracks if a pointer is live but does not care about which
memory object it points to. Second, it uses extra CPU cores to do
dangling pointer scanning and invalidation.

It tracks the liveness of memory object with a shadow memory where each byte
represents 8 bytes of an object. It also has a shadow memory to indicate if
a memory location contains a pointer. A pSweeper-protected program consists
of two parts: the application thread(s) and the Concurrent Pointer Sweeping
(CPW) thread. The application part is the normal program with instrumentation
that registers object information at allocation and pointer information when a
pointer is set.  All live pointers to heap objects are registered in a
linked list.
The CPW thread constantly sweeps the live pointer list to find and invalidate
dangling pointers.

To prevent the situation that an freed object is reallocated before all the
dangling pointers to it are invalidated, pSweeper delays the real free of
an object to the end of each round of pointer sweeping.
Each object's metadata (Figure 5 in the paper) includes a flag of whether
a free call is applied on it; and the metadata are registered in a linked list.
pSweeper intercepts free calls and sets the free flag of an object to true.
The CPW thread sweeps this list to find if an object is waiting to be freed
and if so, mark it as scanned (ready to be freed) and then does the real free
after the sweeping of the pointer list.

pSweeper also embeds information about allocation and deallocation (so-called
Object Origin Tracking (OOT)) in an invalidated dangling pointer.
This helps pinpoint the root cause when a program crashes due to dereferencing
a dangling pointer.

The performance number is pretty good: 12.5% to 17.2% on SEPC CPU 2006,
depending on the sleep time between each round of sweeping.
The memory overhead is not good: 112.5% (no sleep), 169.7% (500ms), and
247.3% (1s).

### What are the strengths of this paper?
- Because of most of the heavy work besides the original program is done in
  a concurrent thread, the performance (wall-clock time) is good.

### What are the limitations and weaknesses of this paper?
- It shared a few limitations with DANGNULL, FreeSentry, and DangSan:
  - could cause program to go wrong due to non-dereference use of dangling
    pointers.
  - does not handle unsafe casts between pointers and integers (could miss
    danglign pointers).
  - does not handle dangling pointers in registers.
- It does not handle unions with both integer and pointers.
- There are "benign" UAF due to delayed free.
- The memory overhead is too high.
- Although the wall-clock running time does not increase a lot for most
  benchmark programs, it uses extra CPU resources. But with the 1s sleep
  interval, it says it only consumes 1% of CPU in the sweeping thread.

### What are other solutions and what are the most relevant works?
- DANGNULL
- FreeSentry
- DangSan

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
- It assumes there are no concurrency bugs in the program, which is fair for
  a research prototype, but in practice how serious concurrency bugs
  could affect it is unclear.
- The mechanism is fairly complex, which means there is a higher chance to
  miss corner cases or have implementation bugs.
