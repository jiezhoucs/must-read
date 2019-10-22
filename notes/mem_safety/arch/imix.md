# Title, Author(s), and Venue
[USENIX Security'18] **IMIX: In-Process Memory Isolation EXtension**

Tommaso Frassetto, Patrick Jauernig, Christopher Liebchen, Ahmad-Reza Sadeghi

### Category and Keywords
**memory isolation**, **memory safety**

### What problem does this paper try to solve?
One way to protect certain types of data such as secret data and
function pointers is to put them into a separate memory region (isolation).
However, how to protect the isolated region from corruption is a problem.

### Why is the problem important?

### What is this paper's solution to the problem?
It adds a new access permission `PROT_IMIX` to virtual memory page,
and a new move instruction `smov`. If the new permission bit is set
on a virtual page, only the `smov` instruction can access this page.
IMIX proposes to put interested data into virtual pages with the
`PROT_IMIX` bit turned on and compile programs to only use `smov`
to access those pages.

### What are the strengths of this paper?
The high-level idea is simple and clear.

### What are the limitations of this paper?

### What are other solutions and what are the most relevant works?
- ERIM

#### Related links

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
Reserved bits of the virtual address is a very scarce resource.
It is not clear to me if the using a reserved bit for the `PROT_IMIX`
is worth it.
