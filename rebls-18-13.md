2/5

- not very clear what is new

# Summary

The paper presents a visual flow-based programming environment to specify
distributed "participatory sensing" applications.
Flow-based programming allows developers to connect the output of nodes into
input of other nodes to form a graph that evaluates whenever a change occurs.
Source nodes generate primary data and sink nodes consume final data.
The proposed "DISCOPAR" supports type-safe acyclic graphs only due to its focus
on non-technical users.
The language offers a variety of predefined nodes for sensing, aggregating, and
visualizing data.
The main aspect of the language is that a single graph can describe the whole
observatory application: from device sensing, to cloud storage and dashboard.
The language is implemented for the browser using RxJS and presents a visual
interface that allows users to search for components, to author the graph in a
canvas through drag-n-drop, and to visualize the result in real time.
The evaluation describes two experiments targeting non-technical users showing
that most of them could program the proposed system.
The first experiment proposes a local sensing application to monitor sound
levels in the environment, display data in a specific format, and upload the
readings to the cloud with additional meta information.
In the second experiment, users were asked to create and deploy a campaign in
one hour.

# Evaluation

The paper reads very well and all ideas are presented very clearly.
However, I found the paper too descriptive and not much technical for an
academic work.
In particular, I missed more details about the semantics of the language,
specially considering the target audience for this workshop.
Maybe the addition of more examples could guide the discussion on the
expressiveness of the language.

Based on the implementation tools, I suppose graph traversal is single
threaded.
What would be the traversal strategy then? What if multiple outputs are active?
I also suppose the components use callbacks internally to avoid stalling the
graph, for example, in network communication.
Nevertheless, I suspect there are still some possible limitations for
time-consuming computations and blocking calls inside these components.
It seems that the language provides no synchronization mechanisms and the paper
does not discuss any consequences.
What if inputs need to be handled together?
I suppose the graph implementation would have to rely on sufficiently large
timers to prevent that inputs dissynchronize.
Is this case relevant for typical applications?
Are nodes allowed to share data? Does the language/interface provides any
mechanism for variables or folding operations?
What does the language cannot express?
Another semantic aspect that is not discussed is on control mechanisms.
Is there any way to stop/pause/switch nodes?
(Maybe there are some control components that are not discussed in the paper.)

Since the focus of the language is on distribution, I also missed some more
details about the underlying architecture.
I suppose a graph description generates an ID or program that can be shared
and deployed in multiple devices and servers to form a "campaign".
Also, it is not clear if the tier separation in Figure 4 (represented as
colors) is explicit or not.
Explicit or not, why is the "Upload" node required?
The Dashboard is barely discussed in the paper.
The visualization in the phone seems to only consider local data, whereas the
dashboard would display the aggregated data from all nodes.
Is that correct?

The first experiment is well described, although I did not understand why it
does not include the distributed part, since its the distinguishing
characteristic of the language.
The second experiment, I did not fully understand.
This is the only phrase I could find describing it more concretely: "Next, the
students were given 30 minutes to program their own campaign and an additional
30 minutes to go out in the field and collect data for their newly created
campaigns."
I found the experiments to be still in early stages to draw any conclusions
about the language.

I wonder if the retired Yahoo Pipes has any relevance in the field of FBP and
if its cloud aspect is related to this work.

Overall, I believe this paper requires more discussion on the expressiveness of
the language and more work on the evaluation.
I would recommend it as a work-in-progress paper.

- Minor issues:

The "DE" and "EE" superscripts are unnecessarily small in comparison with
"DISCOPAR" and I always had to remember their meaning.
I suggest using a more descriptive name.

The phrase "in the case of the" is lost in page 5, 2nd paragraph of 4.1.
