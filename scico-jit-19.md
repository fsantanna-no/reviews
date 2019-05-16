Major Review

# Summary

The paper proposes "guided value specialization" of JavaScript programs for the JavaScriptCore engine for WebKit.
The technique specializes functions based on call sites inside loops in which one or more arguments are invariants and can be treated as constants in the
invocation (hence *value* specialization).
Only "profitable" functions are specialized, i.e., functions with arguments that can lead to real performance improvements.
The *guided* specialization is due to the use of source code annotations to indicate call sites that likely benefit from specialization.

The paper also proposes source-level static analysis tools to (i) finds actual parameters that remain invariant, and (ii) determine formal parameters whose
specialization is profitable.
This way, the guided specialization can be fully automatic.

Since the optimizations are still speculative due to aliasing, the runtime required changes to ensure that the arguments did not change between
initialization and also between multiple invocations.
The technique adopts allocations stamps in all tracked arguments, which are checked on every invocation.

The performance evaluation uses two open benchmarks and two selected applications to illustrate the power of value specialization.
The results show 1.04x average gains with at most 2.47x for the selected applications.

# Evaluation

The paper is too long but also very well written.

The formalization part is economical on explanations and requires more work to be fully graspable.
In particular, the use of small fonts to (partially) explain the figures is annoying.
I'm not sure if the formalization is even required since the algorithms are straightforward and no rigorous analysis is performed on them.

The use of page faults to track changes was discussed very late in the paper and just for a short paragraph.
I believe the paper could give some clues about the page sizes, how many objects fit on them, and what is a typical ratio between specialized/
non-specialized objects sizes and writes.

I also believe the evaluation would be more impartial if it excluded the `rabin-karp` and `image-rotation` tests.
They could be discussed in separate and also include other applications that could benefit from value specialization.
I would be particularly interested in real-world webapps such as GMail and other Javascript-heavy webpages.
A stronger argument would be the fact that the proposed specializations do not degrade neutral applications (such as those in the benchmark), and that they
can considerably boost specific large-scale/real-world applications.

Is it reasonable to perform the static analysis at the server side?
Since the optimization is for the VM, I would expect everything to happen at client side.
I'm not sure how it would affect the evaluation, in particular for real-world applications.

Why aren't real-world applications evaluated at all?
Are they difficult to measure or is due to the lack of time?
Overall, the paper presents solid work but the evaluation lacks more complete applications.

# Editor

I chose "major review" because evaluating real-world applications incurs a lot of work.
Since I'm not 100% confident about this requirement, I would also accept a "minor review" to address the remaining points.
