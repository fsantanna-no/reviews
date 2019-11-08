-2/3: (reject)

# Summary

The paper describes the design and implementation of provenance mechanisms for
HPC Shelf, a general-purpose component-oriented platform for HPC.
It distinguishes between prospective and retrospective provenance mechanisms to
enable traceability and reproducibility features for the HPC framework.

The paper proposes to extend HPC Shelf with "system components", which can be
instantiated with arguments to create actual final parallel computing systems.
The paper presents a case study of four graph-based computations, which can be
properly parameterized and instantiated in the framework.

# Evaluation

This paper is very descriptive about extending a specific system with new
features to support some level of provenance to it.
However, it lacks a critical discussion about the research area.
For instance, it was not clear to me what existing scientific problem the paper
is trying to solve and also what results have been achieved.
The fact that the paper discusses no related work at all makes it even harder
to make critical connections.
I also miss more connections with OO concepts, such as classes, interfaces, and
instances.
The case study just seems to adopt these concepts more abstractly, and hence, I
cannot see many interesting insights in the discussion related to the figures.

- Abstract
    - Very specific and focused on previous work of the authors.
    - "Been interested in introducing features" is not a proper scientific
      motivation.
    - "Reports our results" could be more concrete about the actual results.
    - "Designing and Implementing...". I did not see a discussion about
      implementing the framework (only using it).
- Introduction
    - I miss a discussion about the science behind provenance?
        - Is it about models, theory, performance, usability?
        - What are the existing problems the paper is trying to solve?
    - I also miss a discussion about the prospective and retrospective
        mechanisms.
        - Where do these names come from?
        - Do they cover all provenance types?
- HPC Shelf
    - This section describes a lot of concepts that are, again, very specific
      to previous work: In only 5 paragraphs about 20 concepts have been
      introduced.
    - I wonder if they are all really necessary to understand the rest of the
      paper.
- Provenance
    - Where do these seven levels come from?
    - The fact that none of the data provenance levels are implemented is
      somewhat frustrating, specially because they seem to be harder and also
      more related to the reproducibility mentioned in the introduction.
    - The use of passive voice in some places makes it hard to understand the
      subjects.
- Case Study
    - Why are these examples chosen and how many applications have been created
      with them?
    - Do specialist users tried it or only the authors?
    - The figures are illegible.
- Conclusion
    - The paper describes itself as unfinished and does not yet validates the
      provenance mechanisms themselves.
