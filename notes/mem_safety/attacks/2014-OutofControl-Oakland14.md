# Title, Author(s), and Venue
**Out Of Control: Overcoming Control-Flow Integrity**

Enes Göktas, Elias Athanasopoulos, Herbert Bos, Georgios Portokalidis

[Oakland'14]

### Category and Keywords
**CFI**, **code-reuse attacks**

### What problem does this paper try to solve?
To evaluate the effectiveness of coarse-grained CFI.

### Why is the problem important?

### What is this paper's solution to the problem?
It identifies two new types of gadgets allowed under coarse-grained CFI
(one, two, or at most 3 labels).
One is *Call-stie (CS)* - blocks of instructions right after a call instruction
and terminate with a return instruction. The other is *Entry-point (EP)* -
blocks of instructions starting at a function's entry point and ending
with an indirect branch (Section 3.B says "indirect call or jump" but
Figure 3.b shows a `ret` is also an option; so to my understanding
any indirect branch fits in this category).

By chaining these two types of gadgets, code-reuse attacks are still possible.

### What are the strengths of this paper?

### What are the limitations of this paper?

### What are other solutions and what are the most relevant works?
- Control-Flow Bending
- Control Jujutsu

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?
Coarse-grained CFI is not enough to stop code-reuse attacks.

### Other comments

