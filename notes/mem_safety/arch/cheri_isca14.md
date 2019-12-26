# Title, Author(s), and Venue
**The CHERI capability model: Revisiting RISC in an age of risk**

Jonathan Woodruff, Robert N. M. Watson, David Chisnall, Simon W. Moore,
Jonathan Anderson, Brooks Davis, Ben Laurie, Peter G. Neumann, Robert Norton,
Michael Roe

[ISCA'14]

### Category and Keywords
**capability**, **RISC**, **memory safety**, **tagged memory**

### What problem does this paper try to solve?
Memory safety problems and more.

### Why is the problem important?

### What is this paper's solution to the problem?
It designed and implemented a capability model on the architectural level.
Quoted from the paper
> A *memory capability* is an unforgeable pointer that grants access
to a linear range of address space.

It provides a safe execution environment by unforgeable
`capability` registers and `tagged memory`.
A `capability` contains the base, length, and permissions about
a pointer. These fields are used to decide whether a pointer
have access (read, write, execute) to some memory location.

### What are the strengths of this paper?
- the protection level is very fine-grained: to the byte level.
- The capability has the potential to be extended to realize more
  than memory safety checks. For example, a capability has permission
  bits that specify access permissions.
- The memory access checking is done on the architecture level; so it
  should be fast.

### What are the limitations of this paper?
- It's a new architecture; so the solution cannot be applied to existing
  systems.
- Not handle temporal memory safety problems, such as use-after-free.
- It requires manual annotation for existing programs.

### What are other solutions and what are the most relevant works?
- Hardbound
- Intel's MPX

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
