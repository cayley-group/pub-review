
METHODOLOGICAL STRATEGY

Summary of methodological brainstorm

The previous section presented a loosely-structured brainstorm of ways of advancing the state of the art in biophysical simulation and protein structure inference. In Figure 6, we present a combined summary of the ideas we suggest together with those that were important elements of existing state-of-the-art methods. These ideas are grouped according to categories which we hope will not only help the reader to organize their understanding of what we have presented but be a supportive framework to inspire novel ideation within these categories or building upon the proposed ideas.


Figure 7. Taxonomic/structural summary of possible methods for enhancing biophysical simulation and the inference of protein structures.

Meta-strategy

Given the expanse of possible ways forward and the substantial resources required to try any one approach, we envision that an effort to prototype a subset of these ideas while sharing the larger set will be most effective towards the community collectively optimizing for an optimal combination of these approaches. That is, we hope to share our work early and openly and rely on the scale of the broader community to explore more of this diverse landscape than one group or even consortium can feasibly explore alone. From another perspective, we note that going end-to-end with any one approach isn’t necessarily that difficult - the difficulty comes in choosing the right approach including the possibility of many revisions and improvements of an approach or the need to try multiple approaches. Thus a broadly collaborative effort that spans the broader diversity of approaches can hedge, from a community perspective, against unforeseen strategic shortfalls - especially when efforts overlap effectively such as through genuinely reusable and extensible sharing of model and data processing components.

Further in the domain of meta-strategy is the need for substantial additional input on this document. There is an opportunity to continue to build a broad, eagle eye view of the strategy space (including additional methodological ideas, methodological refinements, and expansion of the review of relevant literature). There is further need to collect unbiased estimates of the usefulness and expense of various approaches. One of the most effective means to this end seems to be to first transform this document into a rather broad review article on the subject to be published in a venue with a permissive attitude about presenting perspectives about what might be tried in the future and use this as a rallying point for input and collaboration and positioning this as an answer to the inevitable question in the community about where to go next after the forthcoming AF2 paper is published.

Flatland simulations as a debugging/development framework

One way to support the development of the system described above would be to develop a simplified testing environment and first ensure the system can perform well there. This kind of approach is essential when seeking to develop complex neural networks (or really any complex software system). It is further important to make a connection with a functional use of the system as early as possible so as to ensure the development of the system remains integrated with the ability to perform that function. Yet in the most initial phase, we will settle for development problems that merely have the same general structure as the full problems and initially need not do so with any level of realism.

One means of accomplishing this task would be to begin by learning to simulate a two-dimensional structure prediction environment (here, “Flatland”, after the 1884 work by Abbot by the same name). The task could be formulated as a design challenge to discover a set of polymer shapes that would “recognize” another set of shapes based on the compatibility of their angles - where one set of shapes is fixed but whose structures are unknown and another set which is to be engineered.

A distance matrix and bond angle matrix could be constructed for the final/solved structure of each shape
An infinity of shapes could be generated
A shape-shape interactome as well as other forms of holography could be generated based on simple complementarity of bond angles or based on simplified molecular dynamics simulations
The shapes could be generated from a simple string code of the same structure as expected amino-acid input strings, such as a decipherable hash function of the concatenated angles of the shape; alternatively, shapes could be evolved according to a simplified evolutionary algorithm, thereby providing evolutionary data
The quality of a shape “drug” for recognizing only one and not other shapes can be directly computed again by way of complementarity of bond angles or simplified MD simulation; i.e. a finished version of the planned system for this simplified system could be taken forwards into a hypothetical use case before developing the larger system

One subtlety of this approach is how to evolve a population of polymers in a manner that is realistic and useful for debugging in advance of training the larger system. We have prototyped a simplified evolutionary optimizer that seems to provide data that can be used either as a ground-truth against which to construct an evolutionary tree or can be used only at the last generation like a set of metagenomic long reads - either might be relevant approaches for training the larger system.

Given a generation of such a population, performing molecular dynamics simulations using Jax MD will reduce development time given the usability of the tool as well as help to build expertise towards later use to pre-train a structure solver from polymer dynamics traces - this package includes an example of training a graph neural network simulator from traces of a 64 Si atom system simulated by a conventional MD tool.

The expense of developing this environment would be the addition of development complexity independent from the primary task - and would be a function of the level of gain expected relative to the ease of subsequently developing the larger system. Alternatively, other means of checking the integrity of the planned means of representing evolutionary information are possible that perhaps need not integrate into an end-to-end preliminary test.

This environment would give us the ability to debug issues such as related to combining non-overlapping datasets (such as, e.g., where not all proteins are reflected in both a crystallography and interactome dataset). Further it would be possible to examine how end-to-end learned physical models of folding dynamics can be evaluated against a holography dataset (such as K’ via H as diagrammed in Figure 8) in a secondary manner than was diagrammed in Phase 2 - e.g. running a simulation of the interaction event.

Jax and a mature foundation for neural network research

The recently released numerical computing library Jax is of dramatic value to the improvement of the productivity of research that involves neural networks. One reason is for the simplicity of the syntax it permits which can be expected to both accelerate the pace of individual researcher progress as well as reduce the likelihood of performance-reducing errors arising from reduced comprehensibility. Further this benefit increases the labor pool and thus, on average, the salary requirements for projects that use it - i.e. it’s easier to find people who can use it since the syntax is almost entirely the same as the popular numerical computing Python library numpy that is a handy tool of most data scientists. Another is the nearly transparent nature by which code can scale across multiple accelerators. And another is the flexibility it provides for implementing complex training schemes of the kind relevant here.


Figure 8. General roadmap structure. A high-level roadmap and intermediate dividends are shown, divided according to phases (0-4) that may be conducted sequentially by a single team or with parallelism over phases 1-3 once a systems integration test suite has been established of the form planned in phase 0.
Points of comparison

One element missing from the above plan currently is how and whether we will make baseline comparisons (i.e. to previously published work) by re-implementing or running published code for these, whether we will simply compare to published results operating on the same problem, or whether we will only make internal comparisons (e.g. own model with and without simulator pre-training). The second and third of these approaches seem to find the best balance of feasibility and informativeness but a group decisions should be made on this far in advance of any manuscript preparation.

Functional outcome and “actual users”

Another need for improvement of the current plan is a deeper study of the design needs of actual users such as through a deeper review of the literature in these areas or by including some “actual users” in an advisory capacity.


