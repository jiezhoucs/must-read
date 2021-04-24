# Title, Author(s), and Venue
[MICRO'19] **CHERIvoke: Characterising Pointer Revocation using CHERI
Capabilities for Temporal Memory Safety**

U of Cambridge

### Category and Keywords
**temporal memory safety**, **CHERI**

### What problem does this paper try to solve?

### Why is the problem important?

### What is this paper's solution to the problem?
CHERIvoke is similar to pSweeper: it delays the free of a heap object,
quarantines it, records the liveness status in a shadow memory region, and
periodically does the real free and sweeps the memory to find and invalidates
related dangling capabilities.

It proposed two new architectural changes to the CHERI architecture to
facilitate the sweeping procedure, which is the main source of the performance
overhead.

First, it add a new instruction `CLoadTags` which only loads the tag of a
capability without loading the capability itself. The sweeping procedure
checks if a memory location contains a capability, and this new instruction
would speed up the check.

Second, it adds a new bit `CapDirty` to a page table to indicate if the
whole page contains at least one capability. The sweeping procedure can
safely skips a whole page whose `CapDirty` is false.

### What are the strengths of this paper?

Built on the CHERI architecture, it takes the advantage of capabilities.
To be more specific, compared with a traditional GC, it is easier to
identify pointers (capabilities) to invoke. There is also more freedom
to modify an experimental architecture than a commercial one.

### What are the limitations and weaknesses of this paper?

### What makes this paper publishable?

### What are other solutions and what are the most relevant works?

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments

