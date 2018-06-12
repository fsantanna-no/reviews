2/5

# Summary

This paper proposes a Actor-Reactor programming model that combines
"active" and "reactive" abstractions.
Actors complement the power of reactors, which cannot easily express typical
functionality of real-world applications such as long-lasting computations and
effectful statements.
Each one of the actors and reactors runs in isolated threads and communicates
through message queues with one another.

# Evaluation

This paper is a good read and proposes a well-thought integration between
actors and reactive programming.
The motivations are clear, the problems are very well stated and well known,
and the solution seems to be effective.
The example, however, seems too artificial but a good starting point.
I like the discussion and distinction between "strongly" and "weakly" reactive.
The common host language and the way the components are connected is also very
well designed.

For me, however, it is not clear which exactly are the contributions of the
paper.
All reactive systems need some form of asynchronous computations to work.
Most (all?) of them have the abstract concept of inputs and outputs which are
very similar to sources and sinks.
Most (all?) of them use queues to avoid concurrency in the graph.
For instance, even the paper acknowledges that FrTime and Elm have similar
interfaces.
The paper states that "their solutions already partially adopted certain
aspects of the Actor-Reactor model".
Why partially?
How does the paper proposal distinguishes from them?
Is the main contribution the adoption of a common host language to express both
models?
Is it the glue language?
Is it the isolation and communication between the actors and reactors?

Another aspect is related to the limitations of the model (if any), which are
not discussed in the paper.
The paper states that "dependencies for actors are dynamic and may thus change
at runtime".
I think this is a very powerful characteristics with critical consequences and
which are not explored in the paper.
As an example, is it possible to handle an arbitrary number of tweets in
parallel?
I can see many possible graphs configurations to deal with this requirement.
In the case, the programmer wants to share a single instance of an actor
among multiple instances of a reactor, I believe she'll need some form of
process IDs to or first-class channels to make it possible.
Another apparent limitation is related to resource management.
Since the actors and reactors are completely isolated, I cannot see how the
behavior of a reactor would affect an actor to avoid memory and CPU leaks.
As an example, some actors may act as sinks and sources when dealing with
requests (e.g., give me a random number).
What happens if the reactor evolves and that request isn't needed anymore?
Will these resources be leaking until the actor terminates (it could take
long)?

The single example does not confront the technical challenges above and only
has 1 input and 1 output.
FRP is good at composing concurrent event sources, such as socket streams,
input devices, and real time.
With a single input and output, there's no reason why the actor would not
handle the tweet itself (also, since a tweet is limited 140 chars, the string
computation inside the reactor would still be O(1)).

I'm not sure if the effectful statement is completely addressed in the paper.
Assuming instantaneous effects (e.g., multiple "print" at the same tick), how
does pushing them to the boundaries help on determinism?
Esterel has an interesting approach to compose and constrain outputs that may
occur concurrently [1].

I also missed some bridges with the world of synchronous languages.
For instance, the second paragraph of Section 2.1 is just a rephrasing for the
synchronous hypothesis.
The term "reactive programming" is biased towards dataflow languages only
(e.g., FRP and the like) [2].
"Communicating Reactive Processes" [3] also reconciles synchronous and
asynchronous computations.
GALS ("globally asynchronous, locally synchronous") is a general architecture
to mix synchronous and asynchronous systems [4].

[1] Berry, Gérard. "The Esterel v5 language primer: version v5_91", 2000 (Section 4.4).
[2] Berry, Gérard. "Real time programming: Special purpose or general purpose languages". Diss. INRIA, 1989.
[3] Berry, Gérard, S. Ramesh, and R. K. Shyamasundar. "Communicating reactive processes". ACM POPL'93.
[4] Teehan, Paul, Mark Greenstreet, and Guy Lemieux. "A survey and taxonomy of GALS design styles". IEEE Design & Test of Computers, 2007.

# Minor Issues

- Instead of pointing to Figure 1, including a concrete graph of the
  application would help a lot.
- Not sure if sections 3.7,3.8,3.9 should actually be subsections of 3.6.
- The term "behavior" is a different concept that appears in FRP and Actors.

# Conclusion

I am not entirely convinced that the paper solves the two problems it poses.
Proposing a 

The paper does not discuss in extent the semantics, the expressive power of the
language and its limitations, i.e., what it can and what it cannot express.
In addition, the provided examples are too simple as evidence of expressiveness.

Supporting two device versions of the same vendor is not a strong evidence of
achieving device independence.

- Problems
    - reinventing/hijacking terminology
        - synchronous languages
            - Elm recognized

    - not sure if the effecful statements have been solved
        - just pushed the effects out of the DAG which at least ensure execution in topological order

## PROS

- The paper motivations, problems involved, and general solutions are clear and feasible.
- The language is well designed.
- The paper is a good read overall.

## CONS

- Contributions are not clear or merely incremental.
- Guiding example is too simple.
- Does not discuss limitations or does not explore all strengths.
- Lacks some bridges with synchronous languages.

## Recommendations

- Be more precise about the contributions.
- Use a more convincing example. Most of my issues would probably be addressed.
