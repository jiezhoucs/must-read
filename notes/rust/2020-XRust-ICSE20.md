# Securing UnSafe Rust Programs with XRust

[ICSE'20] Peiming Liu, Gang Zhao, and Jeff Huang
@Texas A&M

### Category and Keywords
**Rust**, **memory safety**

### What problem does this paper try to solve?
Unsafe Rust code may corrupt memory allocated and used only by safe Rust code.
This paper tries to prevent this.

### What is this paper's solution to the problem?
XRust is a custom memory allocator + program analysis and instrumentation
scheme.  It allocates all heap object accessed by unsafe code to an unsafe
region (those objects are dubbed "unsafe objects"), objects only accessed by
safe code to a safe region, and it instruments **all** code with bound checks to
catch out-of-bounds accesses. (It also provides a guard page solution to prevent
buffer overflow, but guard page is not very strong in general.)

**Object Classification**. It uses a data-flow analysis framework
([PhASAR](https://github.com/secure-software-engineering/phasar)) to find all
memory allocation sites of unsafe objects. As mentioned above, any object
accessed by unsafe instructions are considered an unsafe object.

**Memory Access Instrumentation**. It uses a pointer-analysis framework
([SVF](https://github.com/SVF-tools/SVF)) to identify which instructions
access unsafe objects, and it instruments those instructions to report a
violation when an unsafe instruction accesses a safe object. For pointers
that cannot be resolved by the analysis (i.e., those that may point to either
of the two types of memory), XRust uses shadow memory to dynamically
record if a pointer points to a safe or unsafe object.

The execution performance overhead is 3.6% on median and 21% on average.

### What are the strengths of this paper?
- Targets an important problem.

### What are the limitations and weaknesses of this paper?
- The performance mainly depends on the two program analysis frameworks it uses,
  and since both the frameworks are very conservative, XRust may end up putting
  many safe objects to the unsafe region and instruments many safe instructions.
- It is not very clear how much security improvement is achieved. Considering
  Rust is already very safe, a 21% overhead seems unacceptable.
- Pointer analysis is slow. This paper should report compile time overhead.

### What makes this paper publishable?
- Compared to previous related works (memory isolation for Rust), XRust provides
  much higher coverage of unsafe code.

### What are other solutions and what are the most relevant works?
- Sandcrust @PLOS'17
- FideliusCharm @ACSAC'18

### What is the take-away message from this paper?

### Other comments
- XRust does not handle directly calling malloc-like functions through FFI.
It is not clear how much this would affect the overall security guarantees.
- It only handles the heap.
- It is unclear if the implementation handles all the heap allocation functions.
  The paper mentions `Box` and `Vec::with_capacity`. What about others? Does it
  cover all containers, e.g., `HashMap` and `BTreeSet`?
