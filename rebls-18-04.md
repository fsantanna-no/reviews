# Summary

The paper presents a type-safe multitier reactive language based on the idea of
"placement types", which allows to specify the architecture and implementation
of a complete distributed application in a single file.
Placement types assign specific locations for each piece of data in the
program.
The language offers explicit mechanisms to export and import data across the
host boundaries and aggregators to abstract over individualized remote
accesses.
Two examples illustrate how non-trivial distributed applications can be
implemented in just a few lines of code.

# Evaluation

The paper is over the limit of 6 pages for short papers.

The idea of placement types is neat and the design of the language seems to be
very solid.
The last example at the end of the paper is also very convincing.

My only issue with this paper is regarding its main contribution, which is not
clear.
Since there's already a publication about this work, the text could be more
explicit.
Are there any new design decisions? Is it only a recap? Is it a different focus?
If so, what's left out?
Maybe section 2 could be split in two, one with the recap and another with the
focus/novelties of this work.

I was confused with the terms Signal and Event.
I often see Signal as synonym to Event and Behavior to mean what Signal means
in this work.

The paper says that "local propagation is glitch-free".
Why is this semantics important in the context of distributed applications?
Is it worth to have multiple semantics for the same concept in the language?
I believe the mismatch between synchronous/local vs asynchronous/distributed
graph traversal is impossible to overcome and this fact should be acknowledged.

Just out of curiosity, the paper could describe how the deployment of nodes in
a real network work.

When I started reading the paper I made an immediate connection with the
work on macroprogramming in sensor networks (e.g., Flask and many others).
In the Related Work, the paper cites one of these but in the section about FRP.
I would expect it to be along with the other multitiers or even in a separate
section.
