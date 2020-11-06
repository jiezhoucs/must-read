# Title, Author(s), and Venue
[AsiaCCS'18] **CUP: Comprehensive User-Space Protection for C/C++**

Nathan Burrow, Derrick McKee, Scott A. Carr, Mathias Payer

Purdue University


### Category and Keywords
**memory safety**

### What problem does this paper try to solve?

### Why is the problem important?

### What is this paper's solution to the problem?
This paper designed a hybrid-metadata scheme for pointers and their pointees.
It puts the metadata about a pointer and the pointee to both the pointer itself
and disjoint metadata table. It repurposes a raw C pointer to a so-called
*enriched pointer*:

```C
struct pointer_fields {
    int32 enriched : 1;
    int32 id : 31;
    int32 offset;
}

union enriched_ptr {
    struct pointer_fields capability;
    void *ptr;
}
```

In `struct pointer_fields`, the `enriched` bit indicates if a pointer is
a enriched or a plain C pointer. The `id` is an identifier (or `capability`)
for a memory object; and it is used to index into the metadata table for more
information about the pointee. Each entry in the metadata contains two fields:
the base and the end address of a memory object. The third field `offset`
is used to help compute the current value of the pointer (base + offset).

Upon memory allocation, the pointer is initialized with a new capability ID
and the metadata table gets updated (Listing 2 in the paper) with a new entry
for the memory object. Upon deallocation, the corresponding entry in
the metadata table gets invalidated.
For spatial memory safety, a pointer dereference invokes a check on
if the base plus offset is within the boundary of [base, end].
For temporal memory safety, the check is implicit: as long as there is
a valid entry for the pointee in the metadata table, it means the
memory object is still alive.

### What are the strengths of this paper?
- It provides full memory safety - both spatial and temporal.
- The performance overhead (58%) is better than any other instrumentation-based
  approaches for full memory safety.
- The dereference check is very accurate to the byte level.
  `base <= ptr + element_size - 1 < base + length`.

  *Updated on 10/29/2020*: I thought CUP is the first paper to discuss this but
  it turns out not. The [Low-fat pointer for heap
  paper](https://dl.acm.org/doi/abs/10.1145/2892208.2892212) presents this
  at the beginning of the Background Section. I believe an older paper does
  this too.

  *Updated on 11/5/2020*: The [Baggy Bounds Checking
  paper](https://css.csail.mit.edu/6.858/2012/readings/baggy.pdf) also mentions
  this case.

### What are the limitations/weaknesses of this paper?
- It must transform ALL source code, otherwise the uninstrumented part will
  be incompatible with the instrumented part because of the radical change
  of pointer representation.
  - When parsing arguments to uninstrumented code such as via system calls,
    if the argument is an aggregate type that contains a pointer,
    programmers have to manual annotate the pointer so that the compiler will
    construct the raw C pointer from the enriched pointer.
  - Have to manually instrument assembly code.
  - It's easy to un-enrich an enriched pointer before passing it to
    uninstrumented code. It's not clear, however, how to enrich a raw pointer
    from the uninstrumented to the instrumented world. Uninstrumented heap
    allocator is easy to handle, but what about other functions that return
    a pointer? It looks like it requires programmers to understand the
    uninstrumented code well and do some manual intervention.
    This also means that CUP won't work with pre-compiled binaries.
- It only works for 64-bit systems.
- A single memory object is limited to 4GB. This limitation may not be a
  problem for most programs.
- The number of live memory objects is limited to 2^31 because there are only
  31 bits for capability. But this shouldn't be a problem in practice,
  especially CUP reuses capability ID eagerly.
- Theoretically, the memory overhead could be 32GB - 2^31 16-bytes metadata
  entries.
- It doesn't support multithreading.

### What are other solutions and what are the most relevant works?

#### Related links

### Thing(s) that I like particularly about this paper.
- This paper builds upon a pretty daring idea - repurposing the whole pointer
  for metadata.
- The way it does bounds checking is interesting. See details in the
  *Hardware Enforcement* paragraph of Section 4.2.2. But it's unclear to me
  will it be really faster than a traditional conditional branch approach.

### What is the take-away message from this paper?

### Comments
- One important reason why the scheme is fast is that it trades
  memory for performance.  By reserving a virtual memory region up to 32GB,
  it enables very fast metadata indexing by directly using the capability ID
  as the indexer. This is clearly much faster than other approaches that
  maintain the metadata in splay tree or a hash table.
- The capability ID always starts from 1 and increases by 1. I don't know how
  less secure this is compared with random ID generation.
  Besides, CUP reuses ID eagerly: as soon as a memory object is deallocated,
  its ID will be used for next allocation. This may result in a situation where
  only a small group of IDs are repeatedly used if the program allocates
  and frees memory frequently.
- The paper says "Dereferencing enriched pointers in uninstrumented code
  results, by design, in a segmentation fault.". It's unclear what the
  cost of this mechanism is.

#### Related Work
In the Related Work section, the papers talks too few related work, especially
for temporal memory safety work. Also, it does not make much sense to
criticize those temporal memory safety papers don't handle spatial memory
safety problem.

#### Errors
- There are three errors in the citation list - citations 10 and 11 are
  repeated, citation 41 and 42 are repeated, and citation 8's venue is wrong.1
