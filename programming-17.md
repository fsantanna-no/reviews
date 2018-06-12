-1/2

# Summary

The paper proposes a decomposition strategy for industrial-scale embedded
systems based on a domain-specific language.
The paper first discusses how embedded system development is still dominated by
sequential programming in C due to its efficiency and portability.
However, the reactive and event-based nature of typical embedded applications
is incompatible with sequential execution and imposes an engineering challenge.
The paper discusses possible strategies when handling events and argues that
resource-constrained embedded systems typically adopt the "single entry point
model" in which all event occurrences trigger the same piece of software, i.e.,
a callback.
This strategy generates a monolithic state machine that breaks the standard
ladder of abstraction "instruction -> function -> source file" at the most
essential level of function decomposition.
The paper promotes the use of Céu, a third-party synchronous language that
provides multiple entry points for event reactions and a concurrent mechanism
that crosses reactions, thus restoring the ladder of abstraction.
The paper also presents a real-world communication protocol written in Céu in a
modular way.

# Evaluation

The problem with callbacks and inversion of control is a trending theme with
a number of proposed solutions:
synchronous languages, dataflow and functional reactive programming, and
reactive extensions to general-purpose languages.
For this reason, a pragmatic evaluation of these alternatives based on
real-world industrial applications is welcome.
In particular, the embedded domain is primarily reactive but is still dominated
by C.
Nonetheless, it receives less attention from generic academic forums but
offers a vast playground for evaluation.

The paper does a good job in contextualizing the problem and choosing to focus
only on the engineering aspects of modularization (more specifically,
function-oriented decomposition).
As stated in the paper, most previous work focus on new solutions such as
languages and frameworks, but not much on evaluating existing solutions.

I found the problem description too long and repetitive in the text.
It is a well-known problem with much discussion in previous work.
Nonetheless, the paper brings some novelties to the discussion:
The discussion on the waiting strategies, monolithic implementation, and
abstraction gap seems promising.
However, they are not weaved succinctly or effectively in the text.
I would rather see this discussion condensed in a single section.

The choice for Céu is not justified in extent in the paper.
For instance, I am not convinced that "the imposed administrative runtime and
memory penalty are generally not tolerable in a resource-constrained system".
I have seem multithreading [1], FRP [2], and CSP [3] libraries being
successfully adapted to 8-bit platforms.
In the end, the decision about the language seems to be preconceived, as if the
other alternatives had never been considered for further investigation.
Also, choices involve tradeoffs and the paper mentions the use of C, Céu, and
Rust.
What are the fundamental limitations of Céu that demand these auxiliary
languages?

Regarding the waiting strategies, Figure 3 comes without much clarification
and the burden to depict it is transferred to the reader.
What is the precise meaning of each word in the figure?
The tree view implies a hierarchy among the properties which is not clear for
me.
Why are strategies 5, 11, and 12 not applicable?
How alternative solutions (e.g., FRP) fall in the tree?
How to map each node into a pseudo-code?
(As done for the single entry point model and also with Figure 8.)
Also, I expected the "sweet spot" (8,9) do be discussed together with the
"wrong" choices (not three pages away).

Regarding the abstraction gap and monolithic implementation, Figures 6 and 7
comes (again) without much clarification.
In particular, in Figure 6 Céu has not even been introduced in the paper.
Again, the discussion only considers plain callbacks, while alternatives as
simple as Protothreads [4] offer considerable gains of expressiveness.
Figure 7 shows the state machine for the communication protocol.
Is it a true representation of the protocol?
Is it handmade for this paper?
Is it from a specification document?
Did the authors consider hierarchical state machines to reduce complexity?
How would they fit into the waiting strategies?

Since the paper discusses industrial-scale applications, I would expect
Section 7 to be the longest.
First, the section needs some context.
Is it only about the protocol or there is also an application using it?
Since the "main.ceu" seems to be only about the protocol, how an application is
supposed to interface with it?
Are there any hooks?

Although the example illustrates how reactive code can be modularized, it is
only one small example.
How does this approach scale to larger applications?
How many programs or lines of code have been written using this approach?
If these programs are also available in C, how do they compare?
For instance, is this protocol also implemented in C?
If so, I would expect to see selected chunks for a qualitative comparison.
Besides lines of code, are there quantitative measures to evaluate this
approach?

Overall, I don't find the paper evaluation compelling enough to draw the final
conclusion that "Céu efficiently makes available fundamental software
engineering principles in reactive, embedded systems which are otherwise
inapplicable due to imposed resource limitations."

## PROS

- The discussion on how monolithic state machines are a consequence of the
  waiting strategy that leads to the abstraction gap.

- The insight that a language supporting other waiting strategies can recover
  from the abstraction gap.

- Independent evaluation of a third-party proposal.

## CONS

- Little discussion about alternatives besides callbacks and why they do not
  fit your problem domain.

- Except for Section 7, the sections are too long.

- Lacking evaluation
    - small example
    - no direct comparison to C
    - no quantitative evaluation
    - no clues about other codebases

# General Comments and Suggestions

- Abstract
    - The abstract is too long.

- Introduction
    - "Function-oriented decomposition" is not defined precisely.
    - Why "it seems mandatory that reactive programming languages are complied
      to C"?

- Related Work
    - Maybe the discussion about your previous paper should go to the
      Introduction.
    - Most references about adoption and evaluation are too old (maybe [5]
      helps?).

- Fieldbus Communication Principles
    - I would merge this section with 7, it seems to be a little out of context
      in between 2 and 4.

- Fundamental Event Handling
    - Given the title of the section, I missed some introductory paragraph
      discussing what event handling is about.
    - As commented above, the discussion on waiting strategies needs more work.
    - I did not understand why/how the subsections were split.
    - Figure 5: why not real code from the protocol in C?
    - End of 4.2: this is where the problem with state machines is first
      described (page 7!).

- Monolithic Design
    - "Both are mandatory..." (both what?)
    - Figure 7 needs some context.
    - Since 4.2/4.3 already discusses problems, I believe this whole section
      could fit in Section 4.

- Beyond State Machines
    - Figure 8 (and the discussion in 6.2) clarifies the waiting strategies
      (but is 6 pages away).

- Application Example
    - The text could contain more pointers to the listings.

# References

[1]: ChibiOS:       https://github.com/greiman/ChibiOS-Arduino/
[2]: Flask:         http://dl.acm.org/citation.cfm?doid=1411204.1411251
[3]: occam-pi:      http://concurrency.cc/
[4]: Protothreads:  http://dl.acm.org/citation.cfm?id=1182811
[5]: http://ieeexplore.ieee.org/document/1173191/

# Notes to the Committee

The paper seems premature and even its good aspects require more iterations.
In particular, the application example is too simple to draw the final
conclusion that "Céu efficiently makes available fundamental software
engineering principles in reactive, embedded systems which are otherwise
inapplicable due to imposed resource limitations."
