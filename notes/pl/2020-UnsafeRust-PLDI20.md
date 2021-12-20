# Understanding Memory and Thread Safety Practices and Issues in Real-World Rust Programs

[PLDI'20]
Boqin Qin\*\-, Yilun Chen\+, Zeming Yu\-, Linhai Song\-, Yiying Zhang\#

\*BUPT, \+Purdue, \-PSU, \#UCSD

### Category and Keywords
**Rust**, **memory safety**, **data race**

## What problem does this paper survey?
Unsafe Rust code usages.

### Questions asked by this paper
1. *Why unsafe Rust is used?*
#### By code type
- raw pointer manipulations
- type casting
- calling unsafe functions. Most to functions written by programmers and other
  languages. In the std lib, the heaviest unsafe usages are in the `sys` crates.

#### By reasons
- reusing existing code (e.g., `glibc`)
- improving performance
- bypassing type rules to share data across threads

There are many unsafe blocks that do not contain unsafe code. One reason is
for code consistency (e.g., same function is indeed unsafe on another platform).
The other reason is to use the unsafe labels to warn possible dangers in
using the function, i.e., the operations in the function itself is not unsafe,
but the context of using this function may be unsafe.
One example: https://github.com/tock/tock/issues/1298.

#### Unsafety encapsulation
Interior immutability is dangerous!

2. *What memory safety issues do Rust programs have?*
- *buffer overflows*: A common buffer overflow code pattern: computing a buffer
  size in safe code and dereferencing an out-of-bound location in unsafe code.
  **Reasons**: incorrect checking logic; inconsistent struct status; integer
  overflow.
- *null pointer dereferencing*
- *reading uninitialized memory*: Creating uninitialized memory in unsafe code
  and then using it in safe code.
- *invalid free*: Freeing uninitialized memory is UB.
- *use-after-free*: Freeing an object in safe code and using it later in unsafe
  code. The other way around is also possible, or freeing in unsafe code and
  later using in unsafe code.
- *double free*: Unsafe code may create two owners of an object and later drop
  both of the owners.

### What are the strengths of this paper?

### What are the limitations and weaknesses of this paper?

### What makes this paper publishable?

### What are other solutions and what are the most relevant works?

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
