-2/3

# Summary

The paper proposes LEG, a DSL for gesture-based applications, with two main
goals:
    - specify gestures in a high-level language
    - abstract gesture recognition from specific sensor vendors
The solution involves a "frontend" for end-user gesture programming and a HAL
"backend" for vendor-specific programming.

The Introduction first motivates gesture-based applications as a new
opportunity in computer interaction and discusses the drawbacks of current
low-level SDKs: difficulty in creating new gestures and vendor lock in.
Then, it highlights the paper contributions: a high-level programming language
and the dissociation between the language and the underlying hardware.
Section 2 provides a background for the domain of gestural interactions.
Section 3 presents the syntax, semantics, and the implementation architecture
of LEG.
Section 4 evaluates the expressiveness of LEG to describe gestures and how
effectively the underlying implementation recognizes them.
Section 5 and 6 discusses related work and concludes the paper.

# Evaluation

## Sections 1 & 2

The title "Specification of Gesture-based Applications" is somewhat ambiguous
and suggests that you could program a complete application in the DSL, and not
only recognize gestures with it.

The paper is well contextualized and motivated and I can definitely see a DSL
as a realistic alternative to low-level SDK development.
However, I found the discussion in Sections 1 and 2 too long and a bit
repetitive.
At least for this venue, the discussion about DSLs could be reduced
considerably.
The goal ideas are reasonable and sufficient to fit in a paper.
However, the Introduction does not anticipate the limitations of the proposal
and creates unnecessary expectation to the reader.
Furthermore, the reader only has a concrete idea about the language after
having read about half of the paper, in Section 3.

## Section 3

About the syntax of LEG, the BNF does not seem to be complete:
    - GESTURE is the start symbol. Does it mean that a program can only
      recognize a single gesture?
    - What is 'action', `directions` and `state`?

The description for the semantics is even more incomplete:
    - The actions are not described at all and there are no examples in the
      paper.
        - Can actions be described from gestures? If not, why?
    - How does the runtime matches a gesture?
        - Does it have a context to track the current relation?
        - How does it start/stop tracking?
            - If the user is moving randomly and somehow matches the first line
              of a gesture, is it recognized? Or it needs some idle period to
              start recognizing?
            - The same question goes for tracking stop. If the user continues
              to move after a gesture is recognized, would that invalidate the
              gesture?
            - Therefore, how the language deals with two gestures, one
              "negating" the other? For example:
                - gesture A means "move forward" in a game
                - gesture BA means "don't move forward", where A is a sufix of BA
    - Assuming you could declare multiple gestures in a file (or load multiple
      files):
        - What would that mean?
        - Would them be recognized together until one matches?
        - How does that relate to the previous question?
    - How composable are gestures?
        - Can one define a gesture made of "sub gestures"?
        - Can these "sub gestures" be recognized in parallel?
                - (Ok, the conclusion says they can't.)
        - It seems that constants provide some form of syntactic composition,
          but it is not entirely clear if they are enough.

Another missing semantic aspect is related to the language borders.
How do the gesture recognitions interface with the host application?
Is the main application an event loop? If so, who controls the event loop?
How does the API look like?

The language has some noticeable expressiveness limitations that are not
discussed in the paper:
    - The gesture declarations do not support any kind of arguments, such as
      for configuring joints and relations. For example, receiving 'left' or
      'right' as argument.
    - The gesture declarations do not accept wildcards for pattern matching.
      For example, accepting any of 'left' or 'right' so that the gesture works
      for right and left-handed users.

The paper states that "the architecture of LEG is generic enough to support
different depth sensors" but gives no insights on how it achieves this goal.
It also does not discuss the peculiarities of the two Kinect implementations.

## Section 4

The paper shows a list of gestures implemented with LEG.
It would be interesting to show the number of lines required for each gesture
and how they compare to the original implementations.
Have these new implementations been integrated with (some of) the original
applications?
It would be interesting to show the code for the most complex gesture from the
list.

The paper does not mention if LEG can specify all gestures found in the
literature or if it cannot express some of them (and why not).

Regarding the recognition accuracy, how does it compare with the original
implementations?
The paper mentions that the two subjects of the experiment were instructed via
videos.
Why only two subjects? While repeating the experiment, do they have any
real-time feedback of the success rate? Would this affect the way they perform
the gesture to please the machine? Do they have knowledge about the way the
sensor works or about the semantics of the language?

## Section 5

The syntax and event-based semantics of LEG reminds of synchronous languages.
In particular, Esterel supports a multitude of control mechanisms that can
express event detection, sequences, loops, timers, and parallel compositions
concisely.
It would be interesting to evaluate gesture recognition in these more
expressive languages.

# Summary

I am not convinced that the paper solves the two problems it poses.

The paper does not discuss in extent the semantics, the expressive power of the
language and its limitations, i.e., what it can and what it cannot express.
In addition, the provided examples are too simple as evidence of expressiveness.

Supporting two device versions of the same vendor is not a strong evidence of
achieving device independence.

## PROS

- The paper goals and general solving strategy are clear and feasible.
- The syntax of LEG is realistic for non programmers. 
- The implementation seems to be mature enough.

## CONS

- Lack of discussion on the language semantics:
    - language expressiveness
    - external API
- Lack of discussion and use cases for the HAL.
- Lack of clarification on the experiments.
- Text requires a major grammar review.

## Recommendations

- Be more precise about the language semantics and its limitations.
- Add support for another hardware.
- Extend the evaluation with more complex examples.
