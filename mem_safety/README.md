# Memory Safety related paper.

There is not a unanimous definition on "memory safety". My advisor [John
Criswell](http://www.cs.rochester.edu/u/criswell/index.html) sees memory safety
as "no memory corruption is allowed to happen". My own definition of memory
safety is looser: any behavior relevant to memory violation and protection
is about memory safety. For example, CFI related techniques are not regarded as
"memory safety" by John's definition, as they do not prevent memory corruption;
however, I consider them as memory safety related.

P.S. An obsolete site [Memory Safety
Menagerie](http://sva.cs.illinois.edu/menagerie/) that was maintained by John.
(Theoretically it is still maintained by John but unfortunately it has not been
updated since 2014, the year John got his PhD and joined the [University of
Rochester](https://www.rochester.edu/).
