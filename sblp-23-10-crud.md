# Summary

The paper proposes a DSL to specify CRUD applications for the web.
The DSL looks like a data description language, which specifies the web page
basic properties, database connection, and page layout.
The paper also describes the engine architecture, which is implemented in C++
to support embedded systems.

# Evaluation

The design choices of the DSL are not clearly motivated and justified.
The description of the language is superficial both in terms of syntax and
semantics.
In particular, there is no discussion about the expressiveness of the language.
What is possible to express and what is not possible to express with the DSL?
Since the language seems to be just a data description, why not simply using
JSON?
If not using JSON is justifiable, then what about the DSLs from related work?
The expressiveness of these DSLs is not compared, only their implementations.

About the design choices, the language seems to be untyped, such that numbers
and lists are described as strings.
Why not using richer types to improve readability and provide static checks?
For instance, specifying an array as "id,descr,price" seems to be dispendious
in terms of run time, as well as more error prone.
In this direction of safety, some data description language provide schemas
that can be verified when loading programs.
It seems that this aspect is relevant in the context of the proposed DSL.
The DSL seems to provide a flat syntax with "license.label",
"license.fieldtype", instead of a hierarchical syntax with "licence = { label,
fieldtype }".
This choice goes against standard formats such as JSON and HTML.
It is not clear why choosing a flat syntax, since it seems to be less
expressive.

The paper does not perform any evaluation related to the DSL or the performance
of the framework.
There are not enough evidences that the DSL is appropriate to develop web
applications, and neither that it has sufficient performance to run in embedded
devices.

For this reviewer, the paper seems to be a proof of concept of an evolving
project, but which still requires more rigor in the motivation and evaluation
to become a scientific work.
