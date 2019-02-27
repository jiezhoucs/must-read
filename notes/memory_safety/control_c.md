# Title and Author(s)
[Ensuring Code Safety Without Runtime Checks for Real-Time Control Systems](https://llvm.org/pubs/2002-08-08-CASES02-ControlC.pdf) [CASES'02]

Sumant Kowshik, Dinakar Dhurjati and Vikram Adv

### Category and Keywords
memory safety; real-time systems; c dialect

### What problem this paper tried to solve?
Real-time systems need to perform online upgrades, which introduces untrusted 
code. On memory safety for real-time systems, there are two important aspects
(or challenges) to consider: **overhead** and **error detection**.

### Why the problem is important?
The system must remain stable and operational even in the face of bugs and
malicious code. 

### What is this paper's solution to the problem?
This paper designed a programming language based on C. It is more restrictive
than C so that compiler can perform complete static checking; while it is still
expressive to write sophisticated applications.

### What are the strengths of this paper?

### What are the limitations of this paper?

### What are other solutions and what are the most relevant works?

### What is the take-away message from this paper?
