# Summary

The paper proposes Tachyonn, a markup language as an alternative to LaTex.
It supports math formulas, figures, references, and most expected
functionalities to format scientific papers.
Tachyonn aims to separate content from formatting relying on YAML to hold
definitions and variables.

# Strengths

- Some decisions are very creative: calls, options, short functions.
- Separation between content and formatting via YAML (although not a novel
  idea).
- Borrow ideas from established projects like Markdown, YAML, and AsciiMath.
- The paper is well written. The ideas are very clear. The direct style makes
  the work of the reviewer much easier.

# Weaknesses

- No description for the semantics of functions (or *any* other programming
  mechanism).
- No discussion about templates.
- No discussion about LaTex environments or any other means to extend the
  language with special blocks or syntax.
- No discussion about the expressiveness of the language.
- No complete examples. No concrete comparison with related work.
- No implementation.

# Evaluation

- About the language semantics and expressiveness:

The behavior of most markup commands is straightforward.
However, the paper does not discuss the semantics of functions or other (if
any?) programming mechanisms.
It is not precise what is the effect of a function call in the document.

Some important mechanisms of LaTex are also missing in the paper: templates,
environments, and bibliography.
How to use and define templates? How they distinguish from LaTex.
LaTeX environments provide custom semantics to sections of documents.
How would that be expressed in Tachyonn?
The paper has no discussion about extending the language.
The paper includes a syntax for citations `@[]` but does not discuss how it
works.

It is not clear if Tachyonn is as expressive as LaTex.
If not (probably not), what are the limitations? Which known use cases that
cannot be expressed in the language?
Are functions the only extension mechanisms? What about macros or other
mechanisms to extend the syntax?
What about loops?

- About the implementation:

We are informed about the lack of an implementation only at the end of the
document.
For instance, Section 3.3 suggests that there is an implementation.

The lack of an implementation is very frustrating.
Not because of the parser and analysis per se, but mostly because of the
rendering backend.
It doesn't seem to be a trivial endeavor, specially because it requires another
kind of expertise.

The paper is also not clear about how slides would be supported.

- About related work:

The paper identifies some weaknesses in Pillar and Typst, but does not discuss
them with depth.

About Pillar, it "requires knowledge of Pharo code for making extensions
and lacks strong support for reference management".
What are the problems with "Pharo" and why they do not support reference
management? What about the other features? Could they support references and
make Tachyonn less relevant?

About Typst, it (1) "falls short only in terms of community support", it (2)
"is still in development, has yet to reach a high level of popularity", and (3)
it "combines expressiveness with moderate conciseness".
(1) and (2) do not seem to be relevant weaknesses in scientific terms.
About (3), it is a conclusion based on an analysis of 1 document.
The discussion could compare snippets of the documents to become more
qualitative.

- About the experiments:

Unfortunately, the paper does not show the document being evaluated.
Many important links are hidden in the submission.
Why not using an anonymous repository?
It is very hard to evaluate the experiments without access to the data.

- About the structure of the document:

Section 4 - "Formal Language Specification" is not really formal.
It doesn't seem do add any value to the paper, since the previous section
already describes the language.
Section 6 - "User Perception" seems to be out of place. I was expecting to find
the perception about Tachyonn, but it is about related work. The section could
be moved to Section 2.
