0/2

# Summary

The paper proposes an alternative Adaptive Optimization System for the Jikes
JVM.
It is based on an existing genetic algorithm to optimize AOS configuration
flags.
The main contribution is a multi-level recompilation strategy that tries to use
a greater optimization levels on recompilation.
The paper claims up to 25% better performance with a cost of less that 10% of
the total execution time.

# Evaluation

The paper proposes a very specific modification to a very specific work that
does not seem to be of much relevancy in the academia (at least based on
third-party citations).
For this reason, the paper should stronger motivate its own basis.
The proposed change in the existing SOA algorithm, which dynamically switches
the optimization level on recompilation, is straightforward but also fairly
unsurprising.
Nevertheless, a 25% better performance is definitely worthwhile to investigate.

However, only one of the benchmarks achieve the claimed performance and in a
peek situation.
It would be fairer to lower the claims in a more general context in order to
match the reader's expectations.

The main weakness of the paper (and the reason I am inclined for rejection) is
that it does not include in the benchmarks the genetic algorithm the whole work
is based on.
The only comparison is one phrase after the evaluation:
"Isto é uma vantagem sobre o sistema proposto por Zhao [7], o qual levava cerca
de 15 iterações para apresentar menor tempo de execução em relação ao SOA
original da Jikes."
What exactly was the original gain? Is it visibly worse that the one in this
paper proposal?
How would the original algorithm execute Today (same machine, etc)?

I would also expect other available (and modern) JVMs in the benchmark.
I wonder if the general idea of genetic algorithms is still relevant
considering state-of-the-art JVMs.
The section on related work is very short and could benefit with a discussion
on state-of-the-art JVMs.
In other words, how is Jikes positioned in the spectrum of JVMs in terms of
performance?

# Review

I still consider that the evaluation lacks an appropriate basis of comparison.
This is a paper on performance gains, but the basis of comparison is an
outdated and non-optimized VM.
If the paper wants to compare with Zhao's algorithm it should include it, at
least a reimplementation of it.
Otherwise, it should use a modern environment even if it is harder to modify.
