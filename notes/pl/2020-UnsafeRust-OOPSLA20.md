# How Do Programmers Use Unsafe Rust?

[OOPSLA'20]
Vytautas Astrauskas, Christoph Matheja, Federico Poli, Peter Müller @ETH
Alexander J. Summers @UBC

### Category and Keywords
**Rust**, **Unsafe Rust**, **Software Engineering**

### What problem does this paper try to solve?
Investigating and understanding how programmer use unsafe Rust.

### Why is the problem important?

### What is this paper's solution to the problem?

#### Rust Hypothesis
This paper summarizes an important assumption of Rust, dubbed *Rust hypothesis*:
- Unsafe code should be used *sparingly*.
- Unsafe code blocks should be *straightforward* and *self-contained* to
  minimize the amount of code that developers have to vouch for, e.g., manual
  code review.
- Unsafe code should be *well-encapsulated* behind *safe abstractions* so that
  client code can be written in safe Rust.

This paper aims to (1) assess the validity of the Rust hypothesis and
(2) classify the purpose of unsafe code.

#### Short conclusion
The Rust hypothesis is supported by this study partially: most unsafe code
is simple and well-encapsulated. However, unsafe code is extensively used.
Interoperation with other languages is the most prevalent motivation for
using unsafe code.

#### Six Reason for using unsafe Rust (in three categories)
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

#### Methodology
Five questions in two categories

**The Rust Hypothesis – Do Developers Use Unsafe Rust as Intended?**
1. **(Frequency).** *How often does unsafe code appear explicitly in Rust crates?*
They counted *how many crates contain at least one unsafe block, function,
trait definition, or implementation*. Additionally, they measured the relative
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
(3) a -sys crate, or
(4) any other crate.*

They also measured *how many function calls in unsafe blocks and unsafe
functions are
(a) standard function calls,
(b) calls of trait methods, or
(c) calls of closures or function pointers.*

4. **(Encapsulation).** *Is unsafe code typically shielded from clients through
   safe abstractions?*
They counted *how many unsafe functions are
(1) declared private,
(2) visible within their crate, and
(3) visible to other crates.*

**Measuring the Unsafe World – How do Developers Use Unsafe Code?**
5. **(Motivation).** *What are the most prevalent use cases for unsafe code?*

### What are the strengths of this paper?

### What are the limitations and weaknesses of this paper?

### What makes this paper publishable?

### What are other solutions and what are the most relevant works?

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
The authors assume that the standard libraries are well-vetted and thus
are less likely to have safety problems. I tend to agree with this opinion,
but they may underestimate the amount of unsafe uses due to this assumption.
