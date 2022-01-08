# Retrofitting Fine Grain Isolation in the Firefox Renderer

[Sec'20]
Shravan Narayan(1) Craig Disselkoen(1) Tal Garfinkel(2) Nathan Froyd(3)
Eric Rahm(3) Sorin Lerner(1) Hovav Shacham(1, 4) Deian Stefan(1)

(1) UCSD
(2) Stanford
(3) Mozilla
(4) UT Austin

### Category and Keywords
**sandboxing**, **memory safety**, **Firefox**

### What problem does this paper try to solve?
To sandbox untrusted third-party library code from Firefox renderer.

This paper first summarizes common pitfalls of retrofitting protection to
renderer-library interfaces.

#### Insecure data flow
**Failing to sanitize data.** Data originating from libraries or shared data
accessed by libs should not be trusted and therefore should be sanitized
before use.

**Missing pointer swizzles.** Some sandboxing mechanisms, such as NaCL and WASM,
use alternative pointer representations. Renderer needs to translate or
*swizzle* pointers to and from a target representation when passing them across
the sandbox boundary.

**Leaking pointers.** Leaking renderer pointers to libs may render the system's
ASLR vulnerable.

**Double fetch bugs.** In a concurrent environment, lib code may modify a shared
value after the renderer has checked it before use.

#### Insecure control flow

**Corrupted callback state.** Attackers may corrupt function pointers saved by
renderer and use them to hijack control flow.

**Unexpected callback invocations.** Malicious libs may exploit `longjmp()` and
`setjmp()` to invoke callback functions at unexpected time.

**Callback state exchange attacks.** In a multithreading environment, a
malicious library thread may abusing objects (such as supplying the same object
to different renderer threads while two different objects are expected),
causing UAF or data race.

### What is this paper's solution to the problem?

> RLBox makes data and control flow at the renderer-sandbox interface explicit
through its type system and APIs in order to mediate these flows and enforce
security checks across the trust boundary.

#### Data Flow Safety
All data originating from sandboxed code or shared data accessed by sandbox code
are **tainted**. RLBox distinguishes pointers to renderer memory from pointers
to sandbox memory at the type level (`tainted` or not). Taint can be removed
from a data by validating it.

##### Data flow into the renderer
Mainly two types:
- return value from lib functions
- parameters passed to callback functions from lib to renderer

Programmers need to manually rewrite lib function calls to use RLBox's API
`sandbox_invoke()` and define return type as `tainted`.

Also, data can flow from a sandbox to the renderer via a pointer to the
sandboxed memory. These pointers and the pointed memory need to be `tainted`.
Tainted pointers are restricted to point to sandbox memory.

##### Data flow into the sandbox
Data from the renderer to a sandbox must be either a simple numeric type or a
`tainted` type. Tainted memory should be allocated in a sandbox. Shared objects
between the renderer and sandboxes should be put in the sandboxed memory.
The renderer is restricted to access those memory via `tainted` pointer.

##### Data Validation
RLBox requires developers to write validation functions for `tainted` data.

When tainted data are in sandbox memory, TOCTOU attacks are possible. To prevent
such attacks, RLBox provides an API `copyAndVerify(verify_fn, arg)` to copy
`arg` into renderer memory before validation.

RLBox proposes two styles of writing validators:
- Maintaining application invariants
- Checking library invariants

#### Control Flow Safety
The renderer cannot directly use `tainted` control data, e.g., branching on a
`tainted` variable, but malicious lib code can divert control flow via callback
functions. RLBox provides an API `sandbox_callback()` for developers to register
callback functions. All arguments to a callback function should be `tainted`.

> Specifically, RLBox automatically replaces each Firefox callback passed to
  libjpeg with a pointer to a trampoline function and tracks the mapping between
  the two. When the trampoline function is invoked, RLBox invokes the
  appropriate Firefox callback on libjpeg’s behalf.

(The quoted content is in Section 4.2 but "Control flow safety" is Section 4.4.)

### What are the strengths of this paper?
- Very fine-grained sandboxing: RLBox not only prevents the sandboxed code from
  accessing renderer's memory, but also enforces many other restrictions such as
  which callback functions in the renderers can be invoked.
- Strong evaluation.
- Solved problems in a real-world popular software, and the work was indeed
  adopted in production code.

### What are the limitations and weaknesses of this paper?
- The programmer effort seem moderate.
- Performance and memory overhead are moderate.

### What makes this paper publishable?
- Thorough and robust protection for Firefox renderer against errors in
  libraries.

### What are other solutions and what are the most relevant works?

### Thing(s) that I like particularly about this paper.

### What is the take-away message from this paper?

### Other comments
- Some operations, such as rewriting certain lib functions calls, seems that can
be automatically transformed by the compiler. If so, why did not RLBox do it?

- The engineering effort required to pull off this project is tremendous.

- Related links:
    - [USENIX ;login: version of the paper](https://www.usenix.org/system/files/login/articles/login_winter20_04_garfinkel-tal.pdf)
    - [PL Perspectives blog](https://blog.sigplan.org/2021/07/27/making-software-sandboxing-practical-using-language-based-techniques/)
    - [Securing Firefox with WebAssembly](https://hacks.mozilla.org/2020/02/securing-firefox-with-webassembly/)
    - [WebAssembly and Back Again: Fine-Grained Sandboxing in Firefox 95](https://hacks.mozilla.org/2021/12/webassembly-and-back-again-fine-grained-sandboxing-in-firefox-95/)
    - [RLBox Sandboxing API](https://plsyssec.github.io/rlbox_sandboxing_api/sphinx/)
