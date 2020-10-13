# Title, Author(s), and Venue
Cyclone: A safe dialect of C

Trevor Jim,  Greg Morrisett, Dan Grossman, Michael Hicks, James Cheney,
Yanling Wang

ACT'02

### Category and Keywords
C; programming language; memory safety

### What problem this paper tried to solve?
Memory safety and type safety problems in programs written in C.

### Why is the problem important?

### What is this paper's solution to the problem?
A new dialect of C. It adds new features to C, such as new types of pointers;
and it restricts how C programs should be written, such as pointers must be
initialized before use. It combines static and dynamic analysis. It checks if
a program written in Cyclone violates memory safety while compiling, and warns
programmers about the (possible) vulnerability; and it inserts dynamic checking
when it cannot decide statically.

### What are the strengths of this paper?

### What are the limitations of this paper?

- The change on source code is (a little? or too much?) drastic.
- It lays too much burden on programmers. It not only requires too much porting
  effort but also increase the risk of writing incorrect code: history indicates
  that programmers are fallible species. 
- not backward-compatible
- The `growable region` seems to be unreliable: it relies on programmer's
  annotation. It's highly possible that programmer under- or over-computes the
  region for some data.

### What are other solutions and what are the most relevant works?
TONS of proposed solutions to solve the memory safety related problems caused
by unsafe languages.

The most relevant work is Checked C.

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?
