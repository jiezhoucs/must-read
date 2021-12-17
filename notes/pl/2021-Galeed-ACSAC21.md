## Keeping Safe Rust Safe with Galeed

[ACSAC'21] Elijah Rivera\*, Samuel Mergendahl\+, Howard Shrobe\*, Hamed
Okhravi\+, Nathan Burow\+

\*MIT
\+MIT Lincoln Lab

### Category and Keywords
**Rust**, **MPK**, **memory safety**

### What problem does this paper try to solve?
A Rust binary consists of both safe Rust and unsafe code (unsafe Rust and
third-party libraries). This paper intends to protect the heap used by
safe Rust from unsafe C++ libraries.

### Why is the problem important?
Rust is showing a really promising potential to gradually replace C++ or even C.

### What is this paper's solution to the problem?
Like many prior memory isolation works, Galeed partitions the address space to
two subregions: a safe memory for heap objects allocated by safe code, and an
unsafe one allocated by untrusted libraries. It uses MPK to control the access
permissions of each memory region, i.e., each memory region has its own
permission settings and the code changes access permissions of the protected
region at safe-unsafe code transition boundaries. However, this may be too
restrictive: when untrusted code is executing, it cannot access shared memory
allocated in the safe memory domain.

Galeed proposes a solution called *pseudo-pointer* for this problem.
Essentially, if a pointer to a shared object is passed to and dereferenced by
a lib function, Galeed transforms the pointer to a pseudo-pointer (implemented
as a `struct`) and passes in it instead; it also transforms all the dereferences
to the pointer in the lib function to an API calling back in the Rust code.
In this way, unsafe pointer dereferences are transformed to Rust code,
whose memory safety is guaranteed by the Rust compiler.

### What are the strengths of this paper?
- Works on a really important problem.
- The pseudo-pointer idea is interesting.

### What are the limitations and weaknesses of this paper?

The abstract and intro makes the impression that Galeed protects *ALL*
safe heap objects; however, this is not true. First,  Galeed only targets calls
to C++ libs and ignores calls to C libs. Second, it does not handle unsafe
Rust blocks in the source code. Further, and more significantly, it only handles
one very specific scenario: passing a pointer to a shared `struct` to C++, and
more restrictively, it relies on LLVM's pointer aliasing information to identify
which pointer dereferences in the lib code are from pointer arguments---missing
transforming a pointer dereference to a pointer argument means crashing the
program because the dereference has no memory access to the protected
memory domain.

#### Pitfalls of MPK
The assumption in the threat model that pitfalls of MPK is out-of-scope is
unacceptable. It should at least discuss the potential threats posed by the
pitfalls of MPK specifically for Galeed, even if it does not address them.

#### Others
- Requires the source code or at least LLVM bytecode of target C++ libraries.
- Only evaluated on micro benchmarks, and  even it claims to be a sanitizer for
development purpose, the performance overhead is not low.

### What makes this paper publishable?
- Both Rust and MPK are hot topics.
- The pseudo-pointer idea is worth more thinking.

### What are other solutions and what are the most relevant works?
#### Protecting memory used by safe Rust
- XRust @ICSE'20
- Fidelius Charm @CODSPY'18

#### Memory isolation
Too many to name...
