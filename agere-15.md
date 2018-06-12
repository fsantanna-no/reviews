2/3

# Summary

The paper proposes a reconciliation between the actor model and shared memory concurrency for performance purposes.
To preserve the flexibility of shared memory and prevent race conditions at compile time, the paper proposes a type system based on deny capabilities for
aliases.
The existence of an alias "A" with capability "a" denies the existence of any other local alias "L" with capability "l" or global alias "G" with capability
"g" that doesn't conform with the rules relating "a", "l", and "g" in a matrix of "deny properties".
As an example of an achievement in terms of performance, aliases with "iso" capabilities can be sent and mutated across actors without requiring copies, as they are guaranteed to have no other "unsafe" aliases in the program.

# Evaluation

The "capability matrix" is an interesting contribution and alone worths a paper to discuss each capability more in depth with real-world use cases along with
all implications when combining them.
Even though the paper cites a technical report when introducing the matrix [17], I couldn't find any matrix there.

I'm not 100% sure if the term "capability" is compatible with the one used in the paper cited in the Introduction [24].
Also, the paper says that it "takes a different approach and use *denying* capabilities instead of *allowing* capabilities".
At this point, it is not clear why this difference matters, which justifies some clarification.

I find surprising that the "tag" and "trn" capabilities are a "new form of uniqueness" (in the Introduction).
In particular, the "tag" capability is mentioned in the related work as having a "similar but not identical" counterpart.
Being key contributions of the paper, they deserve a more in-depth discussion, possibly illustrating why/how they are not available in other systems.

The introduction contains too many non-trivial concepts, all being part of the eight(!) paper contributions (e.g., "viewpoint adaptation", "alias burying",
"static region system").
These terms are repeated throughout the text and are only really explained in the formalization (Section 4).
It is not clear how they relate and if they are really orthogonal to count as independent contributions.
In the same line, I believe Section 2 could be expanded to include Tables 2-3 of Section 4 along with an informal but clear description about these terms.
Ultimately, the reader (or potential user) should be able to understand these concepts without understanding the formal type system.

The benchmarks are not conclusive or even speculative on why Pony is faster than the alternatives (other than the phrase "deny properties are amenable to
highly efficient implementation").
As far as I could check, the current implementation is not yet distributed, in contrast with all alternatives.
Are there any trade offs involved?
Furthermore, the paper claims to combine the actor model with shared-memory concurrency for performance, so I would expect a benchmark that takes advantage
of mutation across actors and that compares to a non-actor-based language with unrestricted mutation.
This would also be a strong argument for "non-believers" of the actor model.

Overall, the paper has significant contributions and the presented language seems to be carefully designed.

## Pros
- The capabilities matrix along with the "sendability" and "mutability" properties.
- A formalization for the type system.
- A working (professional) implementation with real users.
## Cons
- No discussion about limitations and trade offs.
- Incomplete implementation (not distributed).
- No comparison with systems that have shared memory.

# General Comments

- Section 1, 5th paragraph:
"What other references to the same object are allowed to do is explicit rather than implied."
I'm confused with this phrase, as I'd expect the opposite.
Given that it is deny based, what an object is allowed is implied by what it is denied to do.

- Sections 1-2:
Given that the terms "reference" and "alias" are somewhat overloaded in CS, the paper could define each in one phrase to avoid confusion.
As an example of overloading, the paper itself uses "ref" as a capability, so one can end up with an "alias to a 'ref' reference".

- Section 2, page 3, first example:
The identifier "next" is not bounded, I supposed it is an argument to "step".

- Section 4:
The formalization explanation is too dry considering that many concepts are only depicted here.
In particular, the tables 1-2 deserve some informal discussion (maybe in Section 2?).

- Section 4, page 4, last two paragraphs:
The references to "fig 2" and "fig 3" should actually be "tab 2" and "tab 3".
