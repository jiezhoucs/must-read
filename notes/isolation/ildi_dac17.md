# Title, Author(s), and Venue
**Instruction-Level Data Isolation for the Kernel on ARM**

Yeongpil Cho, Donghyun Kwon, Yunheung Paek

[DAC'17]

### Category and Keywords
**ARMv8**, **data isolation**, **Privileged Access Never (PAN)**,
**unprivileged load/store**

### What problem does this paper try to solve?
Efficiently performing data isolation in kernel mode to prevent kernel code
accessing certain memory regions.

### Why is the problem important?
Certain types of data needs protection from being corrupted.
Data isolation can be more efficient than providing a complete
memory safety solution.

### What is this paper's solution to the problem?
This paper aims to provide efficient data isolation for programs
running on ARMv8-A processors. It utilizes two ARMv8 features:
the *Privileged Access Never (PAN)* bit, and *unprivileged load/store*
instructions.  When the PAN bit is set, privileged execution (kernel code)
cannot access unprivileged memory regions. When unprivileged load/store
instructions are executed in privileged mode, they act as if they are
unprivileged by checking the unprivileged access permissions of memory
regions.

The high-level idea is simple: when kernel code is executing, set the
PAN bit on, and only use the unprivileged load/store instructions to
access the interested memory region. In this way, most kernel load/store
instructions have no access to the protected memory region.

The solution depends on two invariants: the PAN bit is always on when
kernel code is executing, and the access permissions of the protected
region cannot be changed by the kernel.
It utilizes the `hyp mode` to realize these two invariants.
`hyp mode` is the highest privilege mode which has control over how
the kernel maps memories and configures system registers.
To maintain the first invariant, the `hyp mode` sets the PAN bit,
and all the instructions, e.g., `MSR PAN, <imm|reg>`, that could modify the
PAN bit in the `CPSR` or `SCTLR` register are removed from the kernel.
To keep the second invariant, kernel page tables are configured as read-only,
and all attempts of modifying the kernel page tables are sent to the
the `hyp mode` for verification.


### What are the strengths of this paper?
- Clear and straightforward way of utilizing hardware features.
- This authors showed good knowledge of the ARMv8-A architecture.

### What are the limitations of this paper?
- The application scenarios are limited.
- It only works on ARMv8-A architectures.

### What are other solutions and what are the most relevant works?
- Virtual Ghost

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
- This seems to be another "have a hammer, find a nail" paper.
- Maybe it's due to the page limit, the text of evaluation lacks important
details. For example, which return addresses are protected? How precise
is the CFI implementation?
