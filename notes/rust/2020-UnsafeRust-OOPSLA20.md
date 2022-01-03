# How Do Programmers Use Unsafe Rust?

[OOPSLA'20]
Vytautas Astrauskas, Christoph Matheja, Federico Poli, Peter Müller @ETH,
Alexander J. Summers @UBC

### Category and Keywords
**Rust**, **Unsafe Rust**, **Software Engineering**

### What problem does this paper try to solve?
Investigating and understanding how programmers use unsafe Rust.

### Rust Hypothesis
This paper summarizes an important assumption of Rust, dubbed *Rust hypothesis*:
- Unsafe code should be used *sparingly*.
- Unsafe code blocks should be *straightforward* and *self-contained* to
  minimize the amount of code that developers have to vouch for, e.g., manual
  code review.
- Unsafe code should be *well-encapsulated* behind *safe abstractions* so that
  client code can be written in safe Rust.

This paper aims to (1) assess the validity of the Rust hypothesis and
(2) classify the purpose of unsafe code.

### Short conclusion
The Rust hypothesis is supported by this study partially: most unsafe code
is simple and well-encapsulated. However, unsafe code is extensively used.
Interoperation with other languages is the most prevalent motivation for
using unsafe code.

### Six Reason for using unsafe Rust
(in three categories)
1. **Overcoming Aliasing Restrictions**
    1. Implementing complex data structures
    2. Incompleteness of Rust's type system (Rust may reject safe programs.)

2. **Emphasize Contracts and Invariants**
> ...unsafe serves as a documentation feature: Developers may attach unsafe to
both functions and traits to indicate that their implementation relies on some
contract or invariant that cannot be established by the compiler.

3. **Accessing a Lower Abstraction Layer**
    1. Foreign functions and inline assembly.
    2. Concurrency through Compiler intrinsics.
    3. Performance

### Methodology
Five questions in two categories.

**The Rust Hypothesis – Do Developers Use Unsafe Rust as Intended?**
1. **(Frequency).** *How often does unsafe code appear explicitly in Rust crates?*

They counted *how many crates contain at least one unsafe block, function,
trait definition or implementation*. Additionally, they measured the relative
amount of unsafe code in each crate, i.e. *the ratio of the size of both
unsafe blocks and unsafe function bodies to the total size of the crate.*

2. **(Size).** *What is the size of unsafe blocks that programmers write?*

They counted *how many MIR statements does the compiler generate for unsafe
blocks*.

3. **(Self-containedness).** *Is the behaviour of unsafe code dependent only on
   code in its own crate?*
They measured *how many function calls in unsafe blocks have a call target which
is located in
(1) its own crate,
(2) a crate belonging to the standard library,
(3) a `-sys` crate, or
(4) any other crate.*

They also measured *how many function calls in unsafe blocks and unsafe
functions are
(1) standard function calls,
(2) calls of trait methods, or
(3) calls of closures or function pointers.*

4. **(Encapsulation).** *Is unsafe code typically shielded from clients through
   safe abstractions?*
They counted *how many unsafe functions are
(1) declared private,
(2) visible within their crate, and
(3) visible to other crates.*

5. **(Motivation).** *What are the most prevalent use cases for unsafe code?*

### Empirical Results
1. **(Frequency).** *How often does unsafe code appear explicitly in Rust crates?*
- 76.4% of crates do not contain unsafe usage.
- For 92.3% of all crates, unsafe statements take at most 10%.
- 21.% of crates contain some unsafe statements, and out of those crates,
24.6% have an unsafe statement ration of at least 20%.
- 5.9% of crates contain unsafe trait declarations or implementations.

2. **(Size).** *What is the size of unsafe blocks that programmers write?*
- 75% of all unsafe blocks comprise at most 21 MIR statements.
- 14.4% of tiny unsafe blocks either only wrap an expression or call a single
  unsafe function whose arguments were computed before the unsafe block.
- Conclusion: most unsafe blocks are small.

3. **(Self-containedness).** *Is the behaviour of unsafe code dependent only on
   code in its own crate?*
(Fig. 5–8)
- (Fig. 5) Among all the 772,228 calls in unsafe blocks, 78.3% are to standard functions,
18% to trait methods, and 3.6% to closures and function pointers.
- (Fig. 6) In the entire dataset, 56.3% of the calls are standard functions calls, 42.9%
  are to trait methods.
- (Fig. 7) 52.1% of all functions calls are into the standard library; 25.9% are
  to the same crate; 14.7% are to `-sys` crates; 7.4% are to others.
- (Fig. 8) When only considering calls to unsafe functions, 45.6% are to std.
  lib, 24% to `-sys` crates, 25.9% to the same crates, and 4.4% to others.
- Conclusion: Developers cautiously call unsafe functions that are in other
  crates except they need to interact with system libraries.

4. **(Encapsulation):** *Is unsafe code typically shielded from clients through
   safe abstractions?*
(Table 2 and Fig. 9)
- 88% of unsafe functions are declared as `public`.
- 78.5% of crates have either all or none of their unsafe functions declared
  `public`.
- 34.7% of crates declare unsafe functions that are all hidden from the outside.
- 43.8% of crates declare all their unsafe functions public. These
  crates contain 49.2% of all unsafe functions.
- 59.6% of unsafe functions have foreign item ABI.

5. **(Motivation):** *What are the most prevalent use cases for unsafe code?*
(Table 3)
- 89.76% of all functions that have unsafe usage have call(s) to unsafe
  function, and for 83.5% of such functions, call to unsafe function is the
  only type of unsafe usage.
- 10.3% of functions with unsafe usage contain dereference(s) to raw pointers.
- 93.6% of functions with unsafe usage only have either call to unsafe function
  or dereferences of raw pointer.

#### Motivations of Using Unsafe Code
##### Data Structures with Complex Sharing
- 1.7% of all unsafe functions contain raw pointer dereferences.
- 0.6% of all safe functions contain raw pointer dereferences.
- 7% of all crates contain raw pointers dereferences.
- 6.6% of all crates have types with raw pointer fields.

##### Incompleteness Issues
- 8.9% of unsafe blocks call a `transmute` function. 4.5% of crates use
  `transmute` or `transmute_copy`.
- 1.7% of crates have more than 3 unsafe blocks with `transmute` calls.

##### Emphasize Contracts and Invariants
- 2.5% of trail declarations are unsafe. Five crates account for 40.4% of all
  unsafe trait declarations.
- 36.1% of all unsafe functions are written in completely safe Rust. However,
  many of them are automatically generated to provide peripheral access to
  micro-controllers.

##### Concurrency through Compiler Intrinsics
- Compiler intrinsics are not widely used (possibly because they are marked as
  *nightly-only experimental*).

##### Foreign Functions
- Structure definitions with `#[repr(C)]` account for 3.9% of all structures.
  This annotation is used in 6.2% of all crates.
- Not all crates  that provide bindings to C system libs are suffixed with
  `-sys`.
- 5% of crates contain at least one function with a foreign ABI.
- Only 493 out of 7 million functions use inline assembly, and 10
  hardware-related crates contain 69.8% of all functions with inline assembly.

##### Performance
- Generally, using unsafe code to avoid security checks for performance is not
frequent. However, it is heavily used by certain crates.
- 0.55% of crates contain unsafe blocks that use `MaybeUninit`.

### What are the strengths of this paper?
- It does a much more fine-grained analysis on how unsafe Rust is used compared
  to the [ICSE'20 paper](2020-UnsafeRust-ICSE20.md).

### What are the limitations and weaknesses of this paper?

### What makes this paper publishable?
- It presents many data that facilitate understanding unsafe Rust usage.

### What are other solutions and what are the most relevant works?
- [PLDI'20] **Understanding Memory and Thread Safety Practices and Issues in Real-World Rust Programs**
- [ICSE'20] **Is Rust Used Safely by Software Developers?**
- [TOSEM'21] **Memory-Safety Challenge Considered Solved? An In-Depth Study with All Rust CVEs**

### What is the take-away message from this paper?
The Rust hypothesis is supported in general, but unsafe Rust code is extensively
used.

### Other comments
The authors assume that the standard libraries are well-vetted and thus
are less likely to have safety problems. I tend to agree with this opinion,
but they may underestimate the amount of unsafe uses due to this assumption.
