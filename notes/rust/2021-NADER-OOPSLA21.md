# Safer at Any Speed: Automatic Context-Aware Safety Enhancement for Rust

[OOPSLA'21]
Natalie Popescu(1), Ziyang Xu(1), Sotiris Apostolakis(2), David I. August(1), and Amit Levy(1)

(1) Princeton
(2) Google

### Category and Keywords
**Rust**, **out-of-bounds accesses**

### What problem does this paper try to solve?
Rust programmers can opt out to use the unchecked version `get_checked()` to
index a slice for performance optimization. However, it is unclear whether this
choice of sacrificing security for performance is really effective.

### Why is the problem important?

### What is this paper's solution to the problem?
This paper conducted a study on many popular libraries that use unchecked
indexing and found that 76.4% of their benchmarks only incur little or even a
negative performance improvement. This counter-intuitive fact may be caused by
different compiler optimizations and code layout (affecting how i-cache
performs). Table 2 in the paper summarizes common factors affecting performance.

### What are the strengths of this paper?
- The paper reveals an interesting and possibly surprising fact: unchecked
  indexing for performance purpose may not be justified for many programs.
- The paper is clearly written and easy to read.

### What are the limitations and weaknesses of this paper?
- Only handling one type of dereferences to array elements (`get_unchecked()`).

### What makes this paper publishable?
- A new observation about Rust.

### What are other solutions and what are the most relevant works?
- [ASAP](https://www.unibw.de/patch/papers/oakland15.pdf)

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?
Developers' assumption about programs and the system (compiler, arch, OS, etc.)
may be inaccurate or even in correct. Specific to this paper,

> Developers cannot always correctly identify the most expensive checks to elide.

### Other comments
The abstract oversells a bit. It says

> ..., we present NADER, a Rust development tool that makes applications safer
by automatically transforming unsafe code into equivalent safe code according
to developer preferences and application context.

Although it mentions library bounds checks" in the next sentence, the quoted
sentence gives readers the impression that it handles a lot of unsafe code.
