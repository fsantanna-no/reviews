1/3

# Summary

The paper presents ShillDB, a language for safety in database applications.
The language is centered on the ideas of capabilities and contracts, which can
be applied at the fine grain of function calls.
Capabilities limit the tables a program can access and contracts limit the
operations it can perform on the tables.
ShillDB was used to implement a lending reservation system with reasonable
performance.

# Evaluation

The paper reads well through the supporting example, which definitely enabled a
better overall understanding.
The Introduction seemed too big to me. I suggest to restrict its scope and show
a concrete example ASAP (first appears only at the end of page 5).

Here are my concerns about the paper:

- What are the actors in the process of developing a full safe database
  application? Who writes the capabilities, contracts, and implementations?

It is not clear if it is expected that a single end programmer is responsible
for everything.
If this is the case, then there are less incentives to write safe applications,
since it will take more time (e.g., at the end of the day, programmers choose
the convenience of `scanf` although it is unsafe).
If not, then the capability/contract developer must successfully predict in
advance the minimum needs of the application or he will break the POLP.
I would expect some discussion about these expectations since there is no
usability evaluation in the paper.

- Why is CapQL even required as the end-programmer language?

It seems to me very limiting to expect that programmers will not use SQL for
their everyday queries.
It is not clear to me why CapQL is absolutely required and why cannot the
system simply translate from SQL to CapQL transparently.

- What fundamentally distinguishes a capability from a contract?
  Can't a contract have the same effect of a capability?

I also missed an explicit reference table of the language with all supported
functionalities of capabilities and contracts.
The syntax of contracts is not very user friendly and a I had a hard time to
understand even 1-line contracts without further explanations.
Maybe a description of the syntax and available functionality would help.

- What is the exact semantics of a contract? When does it execute in practice?

Since it is based on Racket's contract system, I believe a short explanation
and example outside the domain of DBs would help to understand it.
I believe some of the explanations in Section 4 (Implementation) are part of
the semantics of contracts and should be moved to Section 3.

- What are the limitations of the language? To what extent it can be used?

Are the presented modifiers expressive enough to provide the intended level of
granularity? How many of them exist? What is the rationale behind them?
Even if the presented contracts did the job for the case study, I was not
convinced that the design is complete.
Overall, the whole Section 3 is very descriptive of some features, but not very
critical about the design and expressiveness of the contracts.
