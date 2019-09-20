# Title and Author(s)
Beyond the PDP-11: Architectural support for a memory-safe C abstract machine
by David Chisnall et al.

### Category and Keywords
abstract machine; C; memory safety; architectural support; fat pointer; 

### What problem this paper tried to solve?
Programs written in C is memory unsafe and are often exploited.

### Why is the problem important?
C-written programs are prevalent. A lot of most important programs, such as
sshd and Linux kernel, are written in C. A memory-safety vulnerability in these
programs could lead to disastrous consequences such as information leaking,
corruption of data, and even the whole system being hijacked.

### What is this paper's solution to the problem?
Provide a safe execution environment on the architecture level. It introduces
a `capability` register besides the regular integer and floating-point register.
`capability` contains the base, length, offset, and permission information about
a pointer. These fields are used to decide whether a pointer have access (read,
write, execute) to some memory location.

### What are the strengths of this paper?
Low-overhead solution to spatial memory safety problems caused by C.

### What are the limitations of this paper?
- It's a new architecture; so the solution cannot be applied to existed computer
  systems.
- Not handle temporal memory safety problems, such as use-after-free.
- It requires manual annotation for existed programs.

### What are other solutions and what are the most relevant works?
#### architectural level
- HardBound (haven't read the paper; don't know how it works)

#### software level
TONS of research have been done to tackle problems caused by the sad fact that 
C is not memory safety. Here are two very incomplete list of the papers, 
[memory safety](https://github.com/jzhou76/must-read/blob/master/memory_safety.md),
[CFI](https://github.com/jzhou76/must-read/blob/master/cfi.md).

### What is the take-away message from this paper?
