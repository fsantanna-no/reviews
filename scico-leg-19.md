In the previous review I spotted just a couple of paragraph modifications in
the paper, therefore I did not provide more feedback.

In comparison with the review I did back in 2017, I did not notice much
improvements in the current version, so I'll repeat most of the comments I did
in the past with some modifications.

# Evaluation

## Section 3

The description for the semantics of the language is incomplete:

- The actions are not described at all and there are no examples in the paper.
    - Can actions be described from gestures? If not, why?
- How does the runtime matches a gesture?
    - Does it have a context to track the current relation?
    - How does it start/stop tracking?
        - If the user is moving randomly and somehow matches the first line of
          a gesture, is it recognized? Or it needs some idle period to start
          recognizing?
        - The same question goes for tracking stop. If the user continues to
          move after a gesture is recognized, would that invalidate the
          gesture?
        - Therefore, how the language deals with two gestures, one "negating"
          the other? For example:
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
            - (Now, the new version says they can.)
    - It seems that constants provide some form of syntactic composition, but
      it is not entirely clear if they are enough.

Now, it is possible to recognize gestures in parallel, but the description in
the paper is again very shallow:

- What it means to be "performed simultaneously"?
    - It is not clear if the beginning of a pose is tracked or only the end
      of it. If I perform the poses in sequence will they be recognized as
      happening simultaneously? This question relates to the second topic
      above.
- Why isn't `;` also a combinator? That would allow to express two sequences of
  poses in parallel. This also relates to the fourth item above about
  composability and expressiveness.
- What if a third pose also occurs simultaneously? Will the combinator be
  still recognized? Is it possible to choose?

Another missing semantic aspect is related to the language borders.
How do the gesture recognitions interface with the host application?
Is the main application an event loop? If so, who controls the event loop?
How does the API look like?

The language has some noticeable expressiveness limitations that are not
discussed in the paper:

- The gesture declarations do not support any kind of arguments, such as for
  configuring joints and relations. For example, receiving 'left' or 'right' as
  argument.
- The gesture declarations do not accept wildcards for pattern matching.
  For example, accepting any of 'left' or 'right' so that the gesture works
  for right and left-handed users.

The paper insists that "the architecture of LEG is generic enough to support
different depth sensors" but gives no insights on how it achieves this goal.
It also does not discuss the peculiarities of the two Kinect implementations to
support this claim.

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

The new subsection about "Productivity Comparison" compares LEG with C#.
Why C# and not related work? What code exactly is being compared? Is it
possible to have a C# library with a similar semantics of LEG? If it is
possible, how would the examples compare? If it is not possible, why not?

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

## Recommendations

- Be more precise about the language semantics and its limitations.
- Add support for another hardware.
- Extend the evaluation with more complex examples.
