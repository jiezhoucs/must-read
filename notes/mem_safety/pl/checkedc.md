# Title, Author(s), and Venue
Checked C: Making C Safe by Extension

Archibald Samuel Elliott, Andrew Ruef, Michael Hicks, and David Tarditi

SecDev'18

### Category and Keywords
C; programming language; memory safety

### What problem does this paper try to solve?
Memory unsafe problems of programs written in C. Currently it only supports
spatial memory safety, mainly on bounds checking.

### Why is the problem important?

### What is this paper's solution to the problem?
It extends C with new types of pointers whose declarations and operations will
be checked statically or dynamically (when static checking does not suffice).

### What are the strengths of this paper?
- It's backward-compatible and allows incremental conversion. 
  Checked C pays very much attention on incrementality. 
- good performance as a lot of checking work is done at compile time.

### What are the limitations of this paper?
- require programmers to rewrite code.
- have only tested small programs. How it scales to large real-world programs 
  is unknown.
- does not provide temporal memory safety.
- When checked code and unchecked code interact, no safety is guaranteed.

### What are other solutions and what are the most relevant works?

- Cyclone
- Rust

#### Useful links
- [Saving C From Cyclone to Checked
  C](https://cs.anu.edu.au/cybersec/issisp2018/assets/slides/cyclone-overview.pdf)

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments

