# Rust

## Unsafe Rust Survey
[PLDI'20] [Understanding Memory and Thread Safety Practices and Issues in
Real-World Rust Programs](https://cseweb.ucsd.edu/~yiying/RustStudy-PLDI20.pdf)
[[notes](notes/rust/2020-UnsafeRust-PLDI20.md)]

[ICSE'20] [Is Rust Used Safely by Software Developers?](https://dl.acm.org/doi/abs/10.1145/3377811.3380413)
[[notes](notes/rust/2020-UnsafeRust-ICSE20.md)]

[OOPSLA'20] [How Do Programmers Use Unsafe
Rust?](https://www.cs.ubc.ca/~alexsumm/papers/AstrauskasMathejaPoliMuellerSummers20.pdf)
[[notes](notes/rust/2020-UnsafeRust-OOPSLA20.md)]

[TOSEM'21] [Memory-Safety Challenge Considered Solved? An In-Depth Study with
All Rust CVEs](https://dl.acm.org/doi/10.1145/3466642?sid=SCITRUS)
[[notes](notes/rust/2021-RustMemCVE-TOSEM21.md)]

[FSE'23] [On the Dual Nature of Necessity in Use of Rust Unsafe
Code](https://www.portokalidis.net/files/unsafe_rust_fse23.pdf)

[WISA'23] [An Analysis of the Rust Programming Practice for Memory Safety Assurance](https://link.springer.com/chapter/10.1007/978-981-99-6222-8_37)

## Secure Unsafe Rust
### Sandboxing/Isolating
[PLOS'17] [Sandcrust: Automatic Sandboxing of Unsafe Components in
Rust](https://www.lamowski.net/docs/plos2017-lamowski-rust-sandboxing-paper.pdf)

[CODASPY'18] [Fidelius Charm: Isolating Unsafe Rust Code](https://almohri.io/papers/fc.pdf)

[ICSE'20] [Securing UnSafe Rust Programs with
XRust](https://peimingliu.github.io/asset/pic/icse-paper1026.pdf)
[[notes](notes/rust/2020-XRust-ICSE20.md)]

[ACSAC'21] [Keeping Safe Rust Safe with Galeed](http://web.mit.edu/ha22286/www/papers/ACSAC21.pdf)
[[notes](notes/rust/2021-Galeed-ACSAC21.md)]

[Sec'23] [TRUST: A Compilation Framework for In-process Isolation to Protect Safe Rust against Untrusted Code](https://www.usenix.org/conference/usenixsecurity23/presentation/bang)

[Sec'24] [METASAFE: Compiling for Protecting Smart Pointer Metadata to Ensure Safe Rust Integrity](https://www.usenix.org/conference/usenixsecurity24/presentation/kayondo)

### Retrofit Memory Safety to Unsafe Rust
[OOPSLA'21] [Safer at Any Speed: Automatic Context-Aware Safety Enhancement for
Rust](http://www.amitlevy.com/papers/nader-oopsla21.pdf)

## Bugs Detection
[PLDI'21] [SyRust: Automatic Testing of Rust Libraries with Semantic-Aware
Program Synthesis](https://dl.acm.org/doi/pdf/10.1145/3453483.3454084)

[SOSP'21] [RUDRA: Finding Memory Safety Bugs in Rust at the Ecosystem
Scale](https://dl.acm.org/doi/10.1145/3477132.3483570)

[CCS'21] [MirChecker: Detecting Bugs in Rust Programs via Static
Analysis](https://www.cse.cuhk.edu.hk/~cslui/PUBLICATION/CCS2021.pdf)

[TOSEM'23] [SafeDrop: Detecting Memory Deallocation Bugs of Rust Programs via
Static Data-flow Analysis](https://dl.acm.org/doi/10.1145/3542948)

## Applying Rust to Secure Stuffs
[ACSAC'20] [RusTEE: Developing Memory-Safe ARM TrustZone
Applications](https://csis.gmu.edu/ksun/publications/ACSAC20_RusTEE_2020.pdf)

## Formal Semantics of Rust
[POPL'18] [RustBelt: Securing the Foundations of the Rust Programming
Language](https://plv.mpi-sws.org/rustbelt/popl18/paper.pdf)

[arXiv'20] [Oxide: The Essence of Rust](https://arxiv.org/pdf/1903.00982.pdf)

## Architecture
[ECOOP'23] [Rust for Morello: Always-On Memory Safety, Even in Unsafe
Code](https://drops.dagstuhl.de/opus/volltexte/2023/18232/pdf/LIPIcs-ECOOP-2023-39.pdf)

## Others
[PLOS'15] [Ownership is Theft: Experiences Building an Embedded OS in
Rust](https://patpannuto.com/pubs/levy15ownership.pdf)

[HotOS'17] [System Programming in Rust: Beyond
Safety](https://www.ics.uci.edu/~aburtsev/doc/crust-hotos17.pdf)

[PLATEAU'18] [Identifying Barriers to Adoption for Rust through Online
Discourse](https://drops.dagstuhl.de/opus/volltexte/2019/10195/pdf/OASIcs-PLATEAU-2018-5.pdf)

[ISSREW'19] [Towards Rust for Critical Systems](https://ieeexplore.ieee.org/document/8990314)

[SOUPS'21] [Benefits and Drawbacks of Adopting a Secure Programming Language:
Rust as a Case Study](https://www.cs.umd.edu/~mwh/papers/rust-adoption.pdf)

[OOPSLA'21][Safer at Any Speed: Automatic Context-Aware Safety Enhancement for
Rust](https://dl.acm.org/doi/10.1145/3485480?sid=SCITRUS)
[[notes](notes/rust/2021-NADER-OOPSLA21.md)]
