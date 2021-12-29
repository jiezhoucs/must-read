# Is Rust Used Safely by Software Developers?
[ICSE'20]
Ana Nora Evans, Bradford Campbell, and Mary Lou Soffa @UVA

### Category and Keywords
**Rust**, **memory safety**

### What problem does this paper try to solve?
It investigates how *unsafe Rust* is used by developers.

### Why is the problem important?
Rust has proven to be an excellent and very promising alternative to C++ or
even C. But it still has security flaws.

### What is this paper's solution to the problem?
The paper focuses on analyzing call graphs of Rust programs to better understand
how unsafe use is propagated.

The paper defines **Possibly Unsafe** as:

> A function may be possibly unsafe if: (1) it is declared unsafe;
(2) it contains an unsafe block; or
(3) it calls a possibly unsafe function.

The third condition is interesting because Rust deems it as safe (called
*safe abstractions*) and even encourages programmers to do so.

#### Core technique
A extended call graph where each node contains not only the function, but a list
of generic type parameters and type substitutions for those when available.

### Questions investigated by this paper

1. **How much do developers use *Unsafe Rust***?

It counts how many the `unsafe` keyword is used in four scenarios (block,
function, trait, and trait implementation).

2. **How much of the Rust code is *Unsafe Rust***?

This is the core question asked by this paper. A *Safe Rust* function may not be
completely safe if it calls a safe API whose implementation actually contains
unsafe code. The paper aims to find out *what percentage of the Rust libraries
lack full safety compiler guarantees?*

3. **What unsafe Rust operations are used in practice?**

The paper wants to understand if interactions with C are the main source of
unsafe Rust.

4. **What ABI (programming languages) are used in the *declared unsafe* functions?**

Whether most called unsafe functions are from external libs implemented in C
or from other Rust libs.

5. **Does the use of Unsafe Rust change over time?**

6. **Why do developers use unsafe?**

#### Results
1. **How much do developers use *Unsafe Rust***?
(Results in Table 1)
- **Crates**: 29% of crates directly include use of *Unsafe Rust*. The most downloaded crates
have a higher use of unsafe (52%). One reason is that they tend to use unsafe
to optimize for performance. Another reason is they often interface with C libs.
- **Blocks**: More than 90% of crates have fewer than ten unsafe blocks.
- **Functions**:
  1. More than 90% of the crates contain fewer than two declared
  unsafe functions.
  2. 69% of the crates that contain at least one declared unsafe
  function actually do not use unsafe operations.
- **Trait and Trait Implementations**: 1.2% and 6% of crates contain unsafe
traits and traits implementations, respectively. Two traits dominate the
landscape: `Send` (30%) and `Sync` (13%).

2. **How much of the Rust code is *Unsafe Rust***?
(Summarized results in Table 2 & 3)
- 44.8% (conservative) and 53.8% (optimistic) crates contain only safe
  functions. For most downloaded crates, the numbers drop to 38.9% and 43.9%.
- On average, a crate depends on 12 other crates.
- 27% of crates neither contain unsafe Rust themselves nor rely on other unsafe
  creates.
- 38% of crates do not have unsafe implementation themselves but depend on
unsafe crates.

3. **What unsafe Rust operations are used in practice?**
(Summarized results in Table 4 & 5)
- Calls to *declared unsafe* Rust functions are a major source.
- The most downloaded crates and `Servo` use C-style pointers more frequently.

4. **What types of *declared unsafe* functions are called?**
- 65% of calls to unsafe functions are to Rust functions, while 22.5% are to
C functions. There are also calls to Rust intrinsics.
- Among the alls to unsafe Rust functions, 47.6% are to *Rust Core Library*,
of which 36.4% are of functions in the `core::ptr` module and 40% are of
functions that are unsafe wrappers to SIMD instructions and arch-specific
intrinsics.
- The most downloaded crates use unsafe Rust intrinsics more often mainly
because of I/O access and common atomic operations.

5. **Does the use of Unsafe Rust change over time?**

Not really.

6. **Why do developers use unsafe?**

The authors did a survey on the Rust subreddit and collected data from 20
respondents.
- For performance (55%)
- Safe Rust being too restrictive (40%)
- Other reasons
    - safe Rust alternative being too verbose or complicated (25%)
    - need to make the code compile (10%)
    - faster to code in unsafe Rust
    - to implement fundamental data structures, custom concurrency primitives,
      system calls, interaction with specilized hardware, and interaction with
      C or other languages

**What operations used by developers that require the unsafe keyword?**
- Calling a non-syscall external C function (45%)
- Calling an unsafe Rust function (25%)
- Working with C-style pointers (25%)
- Working with SIMD intrinsics (5%)

### What are the strengths of this paper?
- It works on a potentially dangerous but not yet well-understood problem---how
dangerous is encapsulated unsafety? This paper does not have a perfect answer
for it but it makes good contributions in this direction.

### What are the limitations and weaknesses of this paper?
- It assumes the Rust standard library is safe.
- For the survey of why developers use unsafe Rust, there were only 20
  respondents.

### What makes this paper publishable?
There were no large-scale survey on how unsafe Rust was used by programs before
this paper. (There are two related survey papers published in the same year.)

### What are other solutions and what are the most relevant works?
- [PLDI'20] **Understanding Memory and Thread Safety Practices and Issues in Real-World Rust Programs**
- [OOPSLA'20] **How Do Programmers Use Unsafe Rust?**
- [TOSEM'21] **Memory-Safety Challenge Considered Solved? An In-Depth Study with All Rust CVEs**

### What is the take-away message from this paper?
Unsafe Rust is used more often than ideal.

### Other comments
There are too many numbers in the Results section and thus it is easy to get
confused. But there seems to be no easy way around it.
