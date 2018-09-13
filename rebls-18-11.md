2/5

# Summary

The paper presents an implementation strategy to compile Statecharts-like
diagrams into readable C code.
As requirements, the translation should yield deterministic execution, not
depend on subtle graphical/typographical details, preserve true concurrency,
produce self-explanatory code, use a safe subset of the host language, and not
rely on preemptive threads.
The paper then describes its "state-based compilation approach" with static
dispatching respecting the sequentially semantics of its guest language
SCCharts.
Finally, the paper evaluates the code generation by asking a group of students
to deduce the original diagrams from the code.
It evaluates time, confidence, and correctness, attesting better results in
comparison to other implementation strategies.

# Evaluation

The paper is very well written and easy to follow.
The implementation strategy is straightforward and well-designed which
definitely count towards the desired readability.

An aspect of the paper that I miss some clarifications is related to the term
"verification".
What kind of properties safety-critical systems need to verify and how do they
relate to the text-to-diagram verification proposed in the paper?

The evaluation could be more explicit about the original diagram(s).
From Table 1, it seems that only one case has been tried, but the text says
"All SCCharts were similar to the example shown in Fig. 3."
In either case, the diagrams are too simple and I wonder how the evaluation
would be affected by more complex examples.
The differences could be even greater due to the translation or maybe become
equally intractable due to state explosion.

In the same line of growing complexity, the paper does not describe more rich
semantics such as suspension and abortion, which are typical in
synchronous languages.
I suppose they can be encoded in the "Core SCCharts" but I believe the
resulting code would not easily resemble the original diagrams.
In particular, abortion seems to be extremely hard to translate because it
affects nested regions and states.

The related work could compare the translation scheme with textual FSM and
synchronous languages, which use similar techniques to the ones described in
the paper.
Most of them are also deterministic and single threaded.
Another source of related work is the field of functional reactive programming
languages, which sort nodes in topological order to respect dataflow
dependencies.
I believe this technique is related to the "sequentially constructive"
semantics of SCCharts.

I'm inclined to reject the paper as full/complete and suggest it as short/in
progress paper.
The reason is that the evaluation section, which is the main argument in
favor of the implementation strategy, does not consider more complex examples
to validate the claims.
