5/7

# Summary

The paper proposes a Java dataflow library for parallel stream processing.
The library expects a graph specification in which vertex are tasks and edges
are data dependencies.
The graph specification allows for parallelization of paths that are not
dependent of one another.
Since it is based on JavaThreads and JavaCL, the library supports heterogeneous
systems with CPUs and GPUs.
The paper evaluates three applications: Volume Ray Casting, Path Tracing, and
Sobel Filters.
All three applications show significant speed ups using the library in
comparison to their sequential implementations.

# Evaluation

The core of the paper (Sections 3 & 4) is straightforward and uses a helpful
guiding example that illustrates the architecture and programming model very
well.
Even though I have no familiarity with this area, I could understand the
example and also infer why it can take advantage of parallelism.
The results seem to be solid but I have no expertise to judge them in
comparison with the state of the art.

The title of the paper is very generic and does not indicate the paper purpose.
Is it the first time that dataflow programming is employed in stream
processing?
If not, I would suggest to use another title.

The paper contributions could be more emphasized in the Introduction (or the
implementation details could be less emphasized).
Would this paper exist only for the fact that it is an alternative to Python
and that is based on threads instead of processes?

The paper presents itself as an "extension" to a previous work, then it uses
the term "inspired by".
After reading the paper, it seems that "inspired by" is more applicable.
How fundamental and indispensable is the adoption of GPUs/OpenCL?

Overall, I missed a more critical vision and opinionated positions in the
paper.
This is related to how the paper exposes its contributions and also on how it
compares itself to previous and related work.
Section 2 is very descriptive about existing work but gives no insights on the
limitations and consequences of not having "support for GPUs nor for
asynchronous communication and concurrent kernel execution".

The guiding example illustrates well the dataflow approach for parallelism but
does not explore much the characteristics that differentiate the library
(namely shared memory concurrency and GPU parallelization) more than
    "with a few nodes invoking the GPU through JavaCL"
and
    "this node runs the `assyncCopyIn` function, which uses the JavaCL context
    in the outer class scope to enqueue the volume data copy into the GPU"
Once again, I missed some critical evaluation in this section.
For instance, how would one describe these nodes without this library?
Would it be harder (e.g., more lines, more auxiliary libraries, etc.) or only
slower (e.g., no GPU)?

The performance results are remarkable, but unfortunately only compared with
sequential versions of the applications.
The Introduction states that "performance comparisons between the two
implementations [JSucuri and Sucuri] are out of the scope of this work".
I did not find a reasonable justification for this statement.
In reality, the *only* comparison I would expect in the paper would be exactly
with the library that inspired this work.

Regardless of any of the pointed issues, the paper is already at a late stage
of development and is more than acceptable for a workshop.
I am sure it will raise interesting discussions at the workshop.

## PROS

- The core of the paper is well written.
- The evaluation and results seem to be solid.
- The chosen applications are real-world applications (and not artificial/toy examples).

## CONS

- The contributions are not clearly stated.
- The performance results are only comparable with sequential versions of the applications.
- The overall tone of the paper is very descriptive but lacks critical insights.
