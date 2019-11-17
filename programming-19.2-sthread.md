1/3

# Summary

The paper presents Sthread, in-vivo model-checking of multithreaded programs.
Sthread relies on C/C++ transparent macro expansions to instrument the original
source code so that it only makes context switches on POSIX calls.
It also requires some explicit annotations by the programmer before shared
memory accesses and use of variables to verify liveness properties.
The focus of Sthread is on the verification of multithreaded
algorithms and not on their actual implementation details.
Because context switching is reduced, the exponential growth of states is
controlled.
In addition, the states of the memory themselves are used as the states in the
model checker, which allows "in-vivo" verification directly on the executable.

# Evaluation

This work seems to be heavily dependent on SimGrid, so it is not clear what are
the exact contributions of Sthread. For instance, the text mentions that
"Sthread is based on recent advances in the SimGrid Software, including a new
"sthread" interface...". This phrase is confusing because it is recursive and
suggests that this new interface is from a third party.
I suggest at least some introduction to SimGrid and Model Checking in separate
to help positioning better the paper contributions.

The Abstract, Introduction and Related Work are somewhat tangled and I suggest
that the first two should be simplified with less references to related work.
All the discussing is too abstract for someone not familiar with this kind of
verification.

I have to admit that the paper really caught my comprehension after the first
concrete example on page 8 (!).
The examples are convincing but still a lot of space is used for source code
but little is used to improve the intuition about Sthread.
For instance, Listing 4 occupies a full page and has absolutely no accompanying
explanations. Why including line numbers if they are never mentioned? Is it
really expected that readers will dig into that page?

The intuition could be much improved if the generated model is depicted at
least for one of the examples. For instance, the tool generates an output that
is never explained in the paper (e.g, page 8):

- Path = 1;1;2;2;1;1
- Expanded states = 10
- Visited states = 13
- Executed transitions = 12

The work is based on the "philosophy that the execution of Sthread should
reflect the underlying concurrent algorithm that is being implemented by the
multithreaded program". The previous paragraph states that "the programmer is
encouraged to place sched_yield() in from of any acess to shared memory".
I'm not completely comfortable with these sentences and the general hypothesis
that Sthread is about finding bugs on the algorithm instead of the
implementation.
This seems to be true only if the annotations and variables are placed
correctly with the help of the programmer, which is also the one who writes the
incorrect algorithm to be verified. I'm convinced of the effectiveness of the
tool, but unease about this apparent "paradox" that could be addressed in the
paper.

The Related Work is very complete and detailed on the technical subtleties, but
again provides little overview or intuition on the differences between the
verification tools. Then, the Conclusion states that Sthread handles a
"variety" of concurrent algorithms. I wonder if it possible to present a more
stable classification of algorithms and properties that could be compared with
related work.
