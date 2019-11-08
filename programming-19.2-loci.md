-1/3

# Summary

The paper discusses the implementation of ScalaLoci, a multitier distributed
programming language, built on top of Scala as its host language.
The implementation relies on Scala's advanced type and macro system so that
ScalaLoci programs retain type safety and access to all Scala facilities
without the need of writing such a complex compiler from scratch.

# Evaluation

The paper sounds like a technical report for a specific audience (the academic
Scala community).
The scientific contributions are not clear in the paper (e.g., "We present our
network communication runtime").
I can conclude that it is possible to create a multitier distributed language
on top of Scala, but what else?
- Should I use Scala to built another distributed multitier language?
- Should I use Scala to built another distributed language?
- Should I use Scala to built another language?
- Should I use Scala to built anything?
I believe the paper should adjust its audience and change the tone to answer
a research question.

Type level and macro programming in Scala is never introduced or even compared
with other languages. For someone unfamiliar with Scala just mentioning "type
level" and "macros" sounds lacking.
What is special about Scala in the context of ScalaLoci?
It is unclear if it would be possible to implement ScalaLoci on top of another
languages with rich meta programming support (Racket, Haskell, etc).
The paper also does not discuss the limitations that are apparent to the end
user (i.e., the ScalaLoci programmer).
Are the error messages good? What did the authors expect to be bad in the first
place? And how did Scala allowed to solve well? What is still unsatisfactory?

The design section is sufficiently detailed, but I still have no idea of how
ScalaLoci solves real distributed problems. All examples that come after are
small and artificial with the sole purpose of describing the code
transformations.
I would expect to see a 10-20 program to highlight the killer language
features.
I would also expect to see that very program translated to Scala (side by side)
to really understand the overall implementation: which translations are macro
expansions, which are type-level manipulation, etc.
The sections that follow are not easy to follow since they are very specific to
Scala. Also, the use of passive voice makes even harder to understand who is
ensuring some property or making the transformation.
These sections are too much descriptive and could have more insights/criticism
about their consequences. The discussions are always centered around Scala with
no attempts to make more general observations.

The "lessons learned" sound more like "suggestions" and are again very specific
to Scala and ScalaLoci. It's also not clear if the upcoming version of Scala
would somehow make the implementation unfeasible.
The runtime section seems completely disconnected from the rest of the paper.
The paper mentions a separate project which raises the flag of over complexity
in the project.
I wonder what is the size of the codebase in comparison to similar systems.
Also, how solid is this codebase to work in the academic setting and how much
of expressive power the end user would loose without Scala.

The related work is mostly about other multitier systems. However, ScalaLoci as
a relevant distributed language has already been peer reviewed.
I would expect the focus to be on DSLs, preferably for distributed systems,
built on top of Scala and other languages with meta programming support.

The conclusion could be much improved and it currently just endorses my own
conclusion that it is possible to implement ScalaLoci on top of Scala, but what
else?
