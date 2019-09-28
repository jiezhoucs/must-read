# Title, Author(s), and Venue
**Protecting Bare-metal Embedded Systems With Privilege Overlays**

Abraham A. Clements , Naif Saleh Almakhdhub , Khaled S. Saab,
Prashast Srivastava , Jinkyu Koo , Saurabh Bagchi , Mathias Payer

[Oakland'17]

### Category and Keywords
**embedded systems**, **IoT**, **ARMv7-M**, **memory safety**

### What problem does this paper try to solve?
There are two serious issues for programs running on bare-metal embedded 
devices.  First, they usually run as privileged, which means they have 
direct accesses to almost all the memory locations and peripherals. 
This is very dangerous. For example, on a ARMv7-M processor, the 
Memory Protection Unit (MPU) configuration can be disabled or dynamically
changed by the program.
Second, they are usually written in C and there are no protection mechanisms
to mitigation all the memory safety problems inherent in C.

In summary, the attack surface is very large under the default setting
of embedded systems. Memory corruption, code injection, control-flow
hijacking, writing to security-critical but system-specific IO, and
modification of registers crucial for system operations are all possible.

This paper works on both of the two problems.

### Why is the problem important?
Embedded devices are being adopted around the world at an alarming rate.

### What is this paper's solution to the problem?
EPOXY consists of four components.
1. specification of access control rules, provided by developers and 
   also compiler.
2. identification of restricted operations from static analysis and
   programmer annotations.
3. privilege overlay: raise the execution privilege level before
   restricted operations and lower it back to unprivileged after the operations.
4. a safe stack

The first three components guarantees that only privileged instructions,
such as *CPS* and *MSR*, can only be executed in privileged mode, and 
also accessing to restricted memory regions, such as memory-mapped registers,
can only be executed in privileged mode.

The fourth component is a protected (safe) stack. EPOXY adopts the SafeStack
from CPI. The original CPI replies on hardware support to isolate the 
SafeStack for low overhead; EPOXY uses a inverse-direction unsafe stack + 
guard region + diversification to protect the safe stack.

### What are the strengths of this paper?

### What are the limitations of this paper?

- Without a mechanism to protect forward-edge indirect branches, the safe
  stack is vulnerable to data corruption, and [ROP is still
  possible.](http://clang.llvm.org/docs/SafeStack.html#known-security-limitations)
- The execution overhead evaluation does not make much sense because the 
  BEEPS benchmarks neither have any privileged nor access sensitive 
  memory regions. So the low execution overhead does not speak too much 
  about the design.

### What are other solutions and what are the most relevant works?
- RECFISH
- Silhouette

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
EPOXY compares its security guarantee with what FreeRTOS provides. 
I don't think it's a fair comparison because FreeRTOS does not gives too 
many thoughts on security.
