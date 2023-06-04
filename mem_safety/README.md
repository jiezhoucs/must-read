# Memory Safety Papers

There is no unanimous definition for "memory safety". My advisor [John
Criswell](http://www.cs.rochester.edu/u/criswell/index.html) sees memory safety
as "no memory error is allowed to happen". My own understanding of memory
safety is looser: it encompasses any behavior relevant to violations and
protections of memory access. For example, CFI related techniques are not
regarded as "memory safety" by John's definition, as they do not prevent
memory corruption. However, I consider them as memory safety work.

The categorization of the memory safety papers in this directory is
mainly inspired by the Section 2 of the [Checked C
Paper](https://www.microsoft.com/en-us/research/uploads/prod/2018/09/checkedc-secdev2018-preprint.pdf).

P.S. There is an related site [Memory Safety
Menagerie](http://sva.cs.illinois.edu/menagerie/) that was maintained by John,
it it seems to become forsaken after John graduated.
