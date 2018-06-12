Overall: -1/3
Confidence: 4/5

# Summary

The paper proposes `nodyna`, a static recommendation system Ruby to refactor
dynamic method and field accesses into static ones.
The goal is to reduce the uses of dynamic constructions that potentially affect
readability, comprehension, and maintainability of code.
`nodyna` categorizes dynamic accesses into 7 refactoring templates and
tries to match them with the source code in order to recommend the
transformations.
The matching algorithm statically infers the set of all possible cases for a
dynamic access and expands them with `if-else` constructs.
The paper claims a refactor rate of 66% for dynamic method invocations, 50%
for field getters, and 33% for setters.

# Evaluation

The paper is well contextualized and motivated, dynamic features offer great
flexibility but involve considerable tradeoffs, such as preventing static
analysis and halving performance.

However, the paper does not discuss how the proposed transformations recover
the desired properties from static code.
Transforming a dynamic code into a static code, does not mean transforming into
a readable, maintainable, efficient static code.
In particular, it seems that that transformations #2, #4, #6, #7 are actually
less readable, maintainable, and efficient.
For instance, dynamic dispatching is typically implemented more efficiently
then cascaded `if-else` statements (e.g., hash tables).
The paper does not discuss in any extent or metrics the quality of the
transformations.
The other transformations, #1, #3, #5 are more effective, but are also trivial.
The paper does not discuss in which context these transformations occur in the
original code.

The evaluation shows that 54/167 are #1 transformations.
I believe the paper should spend more time discussing this extremely common
case.
How do these calls appear on the code?
What is the programmer intention when using a dynamic call that is actually
statically.
In general, I missed a more qualitative analysis of the results.
For instance, there are no samples of the original sources in the evaluation.

The paper mentions that "three projects have been randomly chosen".
What does it mean exactly? Also, why only three? What is the cost of evaluating
other projects?
The evaluation does not measure the size of the codebases to see how relevant
are 167 dynamic instructions.
Also, 3/6 and 1/3 are not significant numbers to appear as 33% and 66%.

The paper does not provide insights about how the tool would apply to other
dynamic languages.
Also, the vocabulary used in the paper assumes some Ruby knowledge.
A brief explanation of the semantics of `send`, `const_get`, and `const_set`
would help the reader.

## PROS

- The context, motivation, and general solving strategy are clear.
- The paper is direct and with a well-delimited scope.
- The implementation seems to be mature enough.

## CONS

- Not convinced that the transformations improve the quality of the code.
- The paper does not discuss in any extent or metrics the quality of the
  transformations.
- The quantitative evaluation needs some clarifications (e.g., size of the codebase).
- No discussion about the application of the proposal in broader contexts.
