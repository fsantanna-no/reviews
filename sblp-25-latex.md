# Summary

The paper proposes Tachyonn, a markup language as an alternative to LaTex.
It supports math formulas, figures, references, and most expected
functionalities to format scientific papers.
Tachynonn aims to separate content from formatting relying on YAML to hold
definitions and variables.

# Strengths

- Some decisions are very creative: calls, options, short functions.
- Separation between content and formatting via YAML (although not a novel
  idea).
- Borrow ideas from established projects like Markdown, YAML, and AsciiMath.

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

Some important mechanisms of LaTex are also missing in the paper: templates and
environments.
How to use and define templates? How they distinguish from LaTex.
LaTeX environments provide specific typesetting effects to section of document.
The paper has no discussion about extending the language.

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

- About the experiments:

