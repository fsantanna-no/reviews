1. Suggestions which would improve the quality of the paper but are not essential for publication:

- Choice for the applications (Abstract & Section-3)

The justification for choosing the applications is that they are
    "well-known stream processing applications",
    "well-known 3-D rendering algorithms", and
    "relevant graphics processing applications".
The paper provides no references and/or arguments that justify the adjectives.

- Previous publication (Section-1)

The paper mentions a Workshop with similar results.
Does a workshop count as a regular publication to justify improvements?
The mention breaks the blind review policy, since it was extremely easy to
uncover the authors.
Also, the paper uses as justification "updated performance" and "additional
concurrency analysis". However, it is not clear exactly how much changes have
been made to justify a new paper (assuming the workshop paper counts as one).

- Capital letters on references (References)

Most references need some proof reading regarding the use of lower/upper-case
letters (e.g., gpu vs GPU, 2Nd vs 2nd, etc.).

2 Changes which must be made before publication:
 
- Fog computing vs paper contributions (Section-1 & References)

The paper makes the case for edge and fog computing which are essentially
distributed computing.
However, AFAIK, the main contributions only apply to local processing since
the framework only supports shared memory for means of communicating.
I would recommend some discussion about this or repositioning the paper
accordingly.

- Shared-memory concurrency (Section-1)

The paper claims that "Java's thread-oriented parallel programming model" is
"often cheaper in terms of processing speed and usage of resources as they
don't require a separate address space".
Even though this claim is the main motivation to propose an alternative
framework, it is merely speculative and is not further elaborated in the paper.
In particular the justification is generic and is not used in the context of
the proposed applications.
How does having an unique address space would speedup the examples?
What are the memory access patterns in these applications?
How does this claim become numbers in the performance evaluation?

- Evaluation only considers serial implementation (Section-3)

The main deficiency of the paper is on its most important section that
evaluates the performance of the framework.
The proposed applications are in the class of "embarrassingly parallel"
problems.
So it would be surprising not to get significant gains in comparison to
sequential implementations.

The paper should take the related work seriously and compare the same
applications implemented with multiple frameworks.
Not even the work which served as the base of this paper is compared in the
evaluation.

3. Confidential comments only for the editor:
