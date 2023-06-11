2/5

# Summary

The paper proposes an architecture to integrate heterogeneous blockchains, such
as Ethereum and Hyperledger Fabric.
The basic idea is to use conversion contracts between the two blockchains.
A local request in the source blockchains triggers a global contract that
converts the request into a uniform format, which is translated on the target
blockchain into its local format, which executes the request, and finally makes 
conversions, now in the opposite direction, towards the source blockchain.
As a use case, the paper illustrates how to request patient records between
blockchains.

# Evaluation

Overall, the paper is too descriptive, but not very critical about the design
of the solution.
It is not clear exactly what is the key contribution about the proposed
architecture.
For instance, how it distinguishes from existing approaches?
The overall idea with the request path "source -> uniform -> target -> execute
-> uniform -> source" is not totally unexpected, so further insights and
justifications could be discussed.
The section on related work is only one page and does not go deep into details.
Considering the proposed architecture of Figure 1, how exactly does related
work compare?
What is unique and unexpected about the paper proposal?
The list of contribution items in the Introduction is generic (e.g., uses
indefinite articles) and does not clearly states the actual contributions.

No specific information or code is given about the contracts and such "uniform
format".
What kind of request is possible?
What kind of request is *not* possible?
How difficult is to define a format that is compatible with both sides?
Maybe the paper should include the complete specification for the patient
record request.
That would give the readers a clear and concrete view of the inner details of
the conversion architecture.

It is not clear how to assess if the proposed solution is successful.
The experiments are focused on comparing the performance of the two
blockchains, which does not seem to answer the main scientific question.
The Performance Evaluation section has no closing remarks, which makes it
difficult to take any conclusions.

In summary, the main reasons why I'm not inclined to accept the paper are as
follows:
    (1) The solution should be justified as a scientific advance in comparison
        with related work. In particular the key aspect of the architecture
        should be highlighted and discussed in detail.
    (2) The expressive power of requests should be discussed in depth, and more
        technical details about the architecture should be presented.
    (3) The experiments should match the paper purpose, and discuss what is
        expected and what is achieved.

Regarding the text and structure of the document, it is well written and
presented.
Nevertheless, some sections are somewhat repetitive about the proposal, as if
they were not connected.
As an example, the idea of "blockchain integration" with "HLF and Ethereum" is
presented a dozen of times across sections, only with rephrasings but without
connections.
Most figures are illegible and I had to zoom into the digital version to
actually read them.

Some assumptions are made, such as relying on CAs and using a pre-configured
blockchain federation.
It is not clear if they are inherent (theoretical) limitations for all possible
integrations to be ever proposed, or only specific to this work.
For instance, a CA may bring an undesired level of centralization.
I believe the Introduction could enumerate the important limitations of the
architecture, if any.

The concrete example only appears at page 10 (!).
This makes much harder to understand the paper, since we can only settle and
refer to some concrete basis much late in the paper.
I would suggest to move the example to much earlier in the paper.

Since the paper does not show in detail the conversion contracts, it is not
clear if they are contracts in the same sense as their in-chain counterparts.
No detailed information about them is provided.
Also, as discussed above, it is not clear what is possible and what is not
possible to express with them.

As suggested above, the Execution Sequence could appear much earlier in the
paper.
I would suggest to be even more concrete in the choice of CGs, CAs, etc, using
real-world names.
The steps should also appear in Figure 3 to associate with the text.
From there, what other kinds of requests could be made?
Which steps would be affected?
What are the limitations?

The Evaluation could discuss what properties a successful architecture should
exhibit.
For instance, no proofs or evidences that it is always possible to convert
contracts across blockchains is given.
Also, what is the complexity to develop such conversion modules?
No code is discussed in the paper.
As discussed above, it is not clear why the performance evaluation is focused
around HLF and ETH.
This does not seem to be the scope of the paper.
All figures are missing the units of measure.
The last tests are only descriptive.
It is not clear why these tests are made, what is expected, and what is
achieved in terms of the proposed architecture.

The Conclusion is only one page, and is composed 1/3 of the context, 1/3 of the
actual work done, and 1/3 of what was not done.
The only explicit conclusion is that "the query processing time of the target
network has major significance on the performance in the overall integration
process", which does not seem to be an evidence that the proposed architecture
is successful.
