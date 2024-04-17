# Summary

The paper proposes a new algorithm to handle cycles in reference counting.
The algorithm uses a single bit of information for unshared objects, which
constitute the majority of objects.
This way, only the meta information related to shared objects, such as counter
and color, needs to be stored in separate.
The algorithm is based on a previous work that extends reference counting
collection with an extra local mark and sweep phase to detect cycles.
The key insight of the new algorithm is to handle shared and unshared object
with slightly modified behaviors to perform some shortcuts for a better
performance.
Even though the proposed algorithm only introduces a marginal improvement over
previous work, it does seem to be relevant for the conference and applicable
systems.

# Issues

However, there are some significant issues with the paper that this reviewer
wants to discuss.

1. Some claims seem to be either exaggerated, unsupported or outdated in some
   form:

- "Reference counting is the memory management technique of most widespread use
   today, used in all operating systems for the management of files and
   processes".

It would be important to list concrete cases that use reference counting and
indicate which algorithm is used.
In particular, it would be interesting to identify the systems that can express
cycles and idicate the actual algorithm.
From the paper, it is not clear what is the state of the art in terms of
academy and industry, since most references are 10-30 years old.
At least in the context of programming languages, reference counting is not
completely prevalent.

- "It takes advantage of the fact that empirical evidence shows that in "real-
  world" applications from 95 to 98% of objects are not shared."

This claim is supported by a reference from 1995.
Note that the paper uses this argument in many places, as a main motivation for
the proposed technique.
Is this claim still valid today? If not, what would be the implication?

- "The new algorithm proposed herein surpasses all its predecessors both
  conceptually and in efficiency, in such a way that this is the most general
  and efficient solution to the problem, reaching the minimum space overhead
  possible in cyclic reference counting."

None of these claims have been rigorously justified in the paper.
The paper does not discuss the time and space complexity of the algorithm in
detail.
In particular, the last part is an absolute claim that would require some kind
of proof.

2. The paper lacks a throughout discussion on related work.

Some discussion appears on the Introduction, but mostly related to previous
work.
Another work appears at the Conclusion, which doesn't seem justifiable.
It is not clear how related algorithms deal with cycles.
In addition, most references date back to early 2000's and late 1990's.
Aren't there any recent advances in reference counting techniques?

3. The paper does not evaluate the algorithm.

The paper only presents an abstract description of the algorithm with no
complex use cases, nor complexity analysis, nor quantitative evaluation.
I would expect some kind of evaluation of the algorithm, such as in terms of
space and time.

The paper mentions a preliminary benchmark that could be presented here.

4. The paper does not discuss practical aspects.

It is not clear if the algorithm has been implemented.
It is not clear in which scenario the authors plan to employ the algorithm.
Is it intended for programming languages?
Are there any plans to substitute existing GCs with the proposal?

# Questions

The triple seems to require a copy of the pointer.
Does every shared pointer requires twice the space plus the counter and color?
How does related work compare in this matter?
Isn't this space overhead significant?

Most phases use recursive definitions.
What would be the impact in the stack growth?

# Minor issues

- The algorithms use a syntax that varies the case of keywords. The indentation
  is not uniform either.
- The name choices for `Mark_red` vs `mark_Red` and `Scan_green` vs
  `scan_Green` is rather confusing. In addition, it also varies using `_` and
  `-`.
- The `mark-Red` pseudo-code breaks in two pages.
- The figures in the examples have low resolution quality. The arrows are
  indistinguishable.
- Section 4 would make more sense if the previous work were compared more
  explicitly in Section 3 (with pseudo code).
- The last paragraph in Section 4 doesn't seem to apply to this work.
