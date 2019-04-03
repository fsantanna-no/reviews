Major Revision

I was one of the reviewers of the original paper on AsyncFRJ and most of my comments still apply to this current submission.
Typically these resubmissions include a text explaining the differences between the papers, but I could not find such discussion anywhere.

# Summary

The paper proposes "AsyncRFJ", a functional reactive language built on top of a simplified and formalized version of Java (Java Featherweight).
The goal is to support reactive dataflow in the context of object-oriented programming.

The paper questions the effectiveness of object orientation for reactive programming and raises awareness for more declarative alternatives to describe data dependencies with automatic updates.

Then, the paper gives some background about FRP, Elm and Featherweight Java (FJ), the two languages that are used as the basis of the proposal.

The core of the paper is the formalization of AsyncRFJ: how it extends the original FJ (e.g., with closures), its core syntax, multi-threading, type system rules, and small-step operational semantics.

Finally, the paper shows a simple example and proofs for properties such as subject reduction and type soundness.

# Evaluation

The paper shows that a significant amount of work has been employed in the proposed language.
The language is fully formalized and has a working implementation.
The paper also demonstrates that the authors have a solid background and knowledge about the area of research.
The use of consolidated previous work (JF and Elm) as its basis is also notable.

The syntax and semantics of the language is placed in the text with not much explanations around them.
The first concrete example appears at page 21 (!!!).
It doesn't seem possible to appreciate all aspects of the language unless one has fluency with formalization of functional reactive languages.
All the discussion that precedes the example is too much descriptive about the precise semantics but with no insights and critical discussion about the choices.
I'd rather see an informal discussion about the language and a deep comparison with related work.
Since the main goal of the paper is to reconcile OO and FRP, the lack of representative examples integrating the two paradigms is questionable.
The toy example in the paper is around 15 lines of code only.
How many applications have been developed with this language? Which features of OO and FRP typically appear on them?
For instance, the example seems to be fully functional with no use of OO features at all.

The two styles are in some sense antagonistic since FRP uses side-effect-free combinators and OO heavily relies on mutation.
I miss this kind of discussion in the paper.
As an example, the reactive subsystem uses threads to prevent blocking the application in asynchronous operations.
How does this subsystem interacts with mutation?
For instance, suppose the `add` behavior calls a method that accesses a private field which is mutated somewhere else in between `async` occurrences.
In such cases, what are the guarantees for the programmer?
FRP is all about concurrency between signals and OO might break it silently.
The `async` support is interesting, but could it be detected automatically when required?
Type soundness is great, but there are other kinds of guarantees such as liveness that are more specific to OO+FRP that could also be explored or discussed.

As someone with a reasonable knowledge on reactive languages, it is still unclear for me what are the exact goals and contributions of the paper.
The related work section does not compare specific aspects of the proposal with other attempts on OO/FRP integration.
As an example, I recall the work on "SuperGlue" which is an FRP extension for Java from the early 2000's, which appear to be in the same design space of AsyncRFJ.
The related work is also restricted to a few works, when this area has been explored in extent.
This way, it is very hard to even identify the paper contributions.
The related work discusses GUI toolkits, I believe this would be an interesting area to explore in the examples since virtually all toolkits are OO based and then programs would be forced to integrate the two styles.
