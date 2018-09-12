4/5

# Summary

This paper presents a case study of writing the orchestration part of a multi-tier chatbot (AI, client and server) in the type-safe synchronous reactive language ReactiveML.
The paper first discusses how to generate a single simple chatbot through type-safe definitions of intents, entities, and dialog (as required by the third-party Watson Assistant chatbot runtime) in OCaml.
It then proposes ReactiveML to build advanced chatbots by composing simpler ones relying on the language's control mechanisms such as processes, parallel compositions, signal communication, and preemption.
The main section dissects the design of a complex chatbot using the techniques discussed in the paper.
The proposed chatbot helps users to create semi-natural language business rules from natural conversations.
As the main challenges, both the chatbot and user may lead the conversation, which creates a shared-memory recursive data structure on the fly.

# Evaluation

The paper showcases a fairly complex system that can be decomposed in much simpler ReactiveML processes through extensive use of control mechanisms.
The paper does a good job on scaling up from a simple non-reactive example, to simple reactive orchestrations, and to higher order compositions.
The final example is also convincing and shows that chatbots are indeed a good target for reactive languages.

My only issue with the paper is related to the lack of discussion on the semantics of processes, specially in the interaction with more advanced control mechanisms (such as `do-until-done`, `control-with-done`, etc).
In particular, I'm uncomfortable with the blocking `message` REST call inside a synchronous process.
I'm assuming it is blocking because it returns the request result.
I'd expect that this process would freeze all other processes in parallel during the whole request.
Also, how does a process with a blocking call interacts with abortion and suspension (e.g., in the *Timeout* example)?

Somewhat related to the issue above, I also miss a discussion on how/why the synchronous model is indispensable in the context of the paper.
Why not using CSP, Go, Erlang, Threads, or another asynchronous concurrency system?

In the last section, the paper enumerates as one of the main challenges to "heavily rely on data sharing between the service and the application".
This is not discussed further and I could not find implicit connections in the text either.

I find Section 3.3 not very well motivated and somewhat disconnected.
I understand that the idea is too present more generic compositions but the examples grow too fast and they are only mentioned again at the end of Section 4.

(If the paper needs more space, I suggest to reduce Section 3, simplify Figure 3, remove Figure 4.)
