# Understanding Memory and Thread Safety Practices and Issues in Real-World Rust Programs

[PLDI'20]
Boqin Qin\*\-, Yilun Chen\+, Zeming Yu\-, Linhai Song\-, Yiying Zhang\#

\*BUPT, \+Purdue, \-PSU, \#UCSD

### Category and Keywords
**Rust**, **memory safety**, **data race**

## What problem does this paper survey?
Unsafe Rust code usages.

## Questions asked by this paper

### Unsafe Usages
#### 1. Why unsafe Rust is used?
##### By code type
- Raw pointer manipulations
- Type casting
- Calling unsafe functions. Most to functions written by programmers and other
  languages. In the std lib, the heaviest unsafe usages are in the `sys` crates.

##### By reasons
- Reusing existing code (e.g., `glibc`)
- Improving performance
- Bypassing type rules to share data across threads

There are many unsafe blocks that do not contain unsafe code. One reason is
for code consistency (e.g., same function is indeed unsafe on another platform).
The other reason is to use the unsafe labels to warn possible dangers in
using the function, i.e., the operations in the function itself is not unsafe,
but the context of using this function may be unsafe.
One example: https://github.com/tock/tock/issues/1298.

#### 2. How unsafe is removed during software evolution?
Dataset: 108 randomly selected commit logs
- Improving memory safety (61%)
- Better code structure (24%)
- Improving thread safety (10%)
- Bug fixing (3%)
- Removing unnecessary usages (2%)

#### 3. How interior unsafe is encapsulated?
Interior immutability can be dangerous. The correctness often relies on how
programmers use the code (e.g., adding proper checks). However, this is not
reliable. Common scenarios that lack checking:
- Using return values of unsafe functions (including FFI)
- Directly dereferencing input pointers
- Using input index to access memory
- Using function pointers
- Type casting (including changing objects' lifetime)
- Accessing uninitialized memory

One particularly dangerous code pattern is messing up the mutability of a
reference inside a unsafe block: code in an unsafe code can use an immutable ref
argument to mutate the referent. The [TOSEM'20 Rust CVE survey
paper](2021-RustMemCVE-TOSEM21.md) calls such behavior "unsound API".

### What memory safety issues do Rust programs have?
- **Buffer overflows**. A common buffer overflow code pattern: computing a buffer
  size in safe code and dereferencing an out-of-bound location in unsafe code.
  *Common culprits for failed checking*:
    - Incorrect checking logic
    - Inconsistent struct status
    - Integer overflow.
- **Null pointer dereferencing**
- **Reading uninitialized memory**: Creating uninitialized memory in unsafe code
  and then using it in safe code.
- **Invalid free**: Freeing uninitialized memory is UB and dangerous.
- *Use-After-Free*: Freeing an object in safe code and using it later in unsafe
  code. The other way around is also possible, or freeing in unsafe code and
  later using in unsafe code.
- *Double free*: Unsafe code may create two owners of an object and later drop
  both of the owners.

### What are the strengths of this paper?

### What are the limitations and weaknesses of this paper?
- The unsafe code cases were selected *randomly*.

### What makes this paper publishable?
- Early work analyzing unsafe Rust code usages.

### What are other solutions and what are the most relevant works?
- [ICSE'20] **Is Rust Used Safely by Software Developers?**
- [OOPSLA'20] **How Do Programmers Use Unsafe Rust?**
- [TOSEM'21] **Memory-Safety Challenge Considered Solved? An In-Depth Study with All Rust CVEs**

This paper differs from the ICSE and OOPSLA paper in that the authors manually
analyzed unsafe code usages and bugs, while the other two survey paper
mainly used tools to automatically collect facts about unsafe Rust usages in
a large code corpus.

### Other comments
- Some of the *insights* and suggestions summarized by this paper are actually
  common practices suggested by Rust. So in this sense the paper oversells a bit.
