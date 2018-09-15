3/5

# Summary

This short paper contrasts two FRP architectures: Elm's single reducer that
applies to the whole global model, and Reflex's multiple local reducers that
apply to more explicit sub-states.
The main section of the paper compares the implementation of a TODO-MVC
application focusing on the behavior of the list of TODO items.
In Elm, the implementation is scattered across the whole file and requires
"CTRL-F" queries to understand the behavior as a whole.
If Reflex, the behavior is self-contained in a single portion of code.
The paper then discusses the tradeoffs between the architectures with respect
to dependencies, familiarity, easy of reading and writing, and serialization.

# Evaluation

The paper raises an interesting discussion about what would be the best
architecture for FRP applications.
I'm not an expert in FRP but could understand the central discussion and main
arguments in the paper.
However, I believe the text could introduce what is described as the
fundamental difference between the languages, namely high-order and cyclic
streams (also the concept of Dynamics).
Furthermore, the text does not discuss *why* these features are necessary to
maintain explicitness in FRP.

In general, the examples and explanations are too short and demand more
familiarity with Haskell (specially for the examples in Reflex).
For instance, from the example, I could not fully acknowledge the phrase "In
Reflex we use stream combinators to define the model and view as streams of
each other. The single global I/O cycle of Elm becomes a number of cyclic
definitions between model and view streams in Reflex."

The TODO-MVC example focus on understanding what are the pieces of code that
affect the "entries".
What if we wanted to know what a specific message may affect in the program?
In this case, the implementation in Elm would be the one to provide the answer
without a "CTRL-F".
Why is this question less important (or irrelevant) than the one raised in the
paper?

One aspect that the Reflex's architecture seems to be superior is on lexical
scope: "There's also a subtler way the Elm Architecture undermines
explicitness: each piece of state can be modified in terms of any other piece
of state. There's no explicit isolation between independent states."
This aspect is not further investigated in the paper.
I wonder how a short-lived object such as editing an entry in the list would
be implemented.
I suspect that Elm would require some form of explicit state machine in the
global state that Reflex could somehow avoid.

The section on related work seems to be quite incomplete.
The paper only provides 4 references (one is a Wikipedia entry which is not
peer reviewed).

If the paper needs more space, I believe Section 7 on future work could be
removed.
