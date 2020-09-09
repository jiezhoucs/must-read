# Memory Safety Papers

There is not a unanimous definition of "memory safety". My advisor [John
Criswell](http://www.cs.rochester.edu/u/criswell/index.html) sees memory safety
as "no memory error is allowed to happen". My own definition of memory
safety is looser: any behavior relevant to violation and protection of memory
access
is about memory safety. For example, CFI related techniques are not regarded as
"memory safety" by John's definition, as they do not prevent memory corruption;
however, I consider them as memory safety related.

The categorization of the memory safety papers in this directory is
mainly inspired by the Section 2 of the [Checked C
Paper](https://www.microsoft.com/en-us/research/uploads/prod/2018/09/checkedc-secdev2018-preprint.pdf).

P.S. There is an "obsolete" site [Memory Safety
Menagerie](http://sva.cs.illinois.edu/menagerie/) that was maintained by John.
(Theoretically it is still maintained by John but unfortunately it has not been
updated since 2014, the year John got his PhD and joined the [University of
Rochester](https://www.rochester.edu/).
