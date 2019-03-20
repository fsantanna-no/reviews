-2/3

# Summary

The paper presents TaskFlow, a domain-specific language built on top of iTasks
for "task-oriented programming".
The goal is to offer a language more palatable for non programmers.
The approach is to offer interchangeable textual and visual representations of
programs.
The central concept of the language are "Tasks", which represent functional
combinators that use typed links to form a workflow.
The main combinators are sequences, conditionals, and forks.

# Evaluation

The paper is easy to follow and very descriptive about the proposed language.
However, I missed a more critical vision of the presented ideas in comparison
to related work.
In particular, since the work is based on iTasks, I would expect some code
snippets for the same guiding example for a more concrete comparison.

The paper assumes that "Task Oriented" is a known paradigm, but it seems that
iTasks is the only language to explicitly embrace it.
In order to better motivate the paper, I would expect a more elaborated
introduction to business processes, workflows, and the whole idea of
task-oriented programming.
Overall, the proposed language seems to be excessively tightened to iTasks, and
the core insights and contributions of the paper became unclear or, at least,
not completely independent from iTasks.

Regarding the discussion on the expressiveness (and lack of), I believe the
paper can be much improved.
First, it uses different names for typical programming mechanisms.
The paper could at least start with analogies to variables, sequences,
conditionals, loops, etc., and then discuss the differences.
Then, it could discuss what's not there.
For instance, the lack of a loop construct is surprising and not discussed at
all!
The paper has no throughout discussion of the limitations of the language.
For instance, which obvious features could not be added to the guiding example?
Why not and what are the consequences?
I could not find the actual semantics of the parallel construct.
What if two branches access the same shared data?
How do exactly they execute?
What do I have to worry and what I don't have to worry about concurrency
problems?
In future work, the paper mentions the lack of unilateral termination of the
parallel construct.
This mechanism is far from trivial (e.g., presence of shared memory, locks,
open resources, etc.) and is discussed in extent in the community of
synchronous languages (e.g., see "Preemption in concurrent systems").
Synchronous languages support events, logical parallelism, abortion, shared
memory, and determinism, and seem to cover the semantic requirements of
task-oriented programming.
I suggest to compare with them in related work.

There is no evaluation of the language in the paper, such as user studies,
discussion of complex examples, evaluation of complete applications, etc.
In the end, we have no strong evidences that the contributions are actually
delivered.

I like the problem, I like the design, and I like most of the text.
However, my opinion is that the paper submission is yet precipitate.
If the paper is not accepted, I would recommend a less descriptive text in
favor of more critical discussion.
