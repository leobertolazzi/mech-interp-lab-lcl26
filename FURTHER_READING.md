# Further Reading and Tools

This document is a curated starting point for studying mechanistic interpretability beyond today's lab. It is not an exhaustive bibliography. The entries prioritize foundational papers, maintained libraries, open tutorials, etc.

## Resources Directly Related to the Lab

The following resources are foundational to the two notebooks and the experiments performed during the lab.

### Notebook 01: Linear Representations and Steering Vectors

- [Representation Engineering: A Top-Down Approach to AI Transparency](https://arxiv.org/abs/2310.01405) studies representations and interventions at the level of model activations rather than individual neurons.
- [Steering Llama 2 via Contrastive Activation Addition](https://arxiv.org/abs/2312.06681) is the closest reference for the notebook's contrastive difference-in-means steering procedure.

### Notebook 02: Sparse Autoencoders and Feature Interventions

- [Sparse Dictionary Learning](https://en.wikipedia.org/wiki/Sparse_dictionary_learning) provides the mathematical background for representing an activation as a sparse combination of learned dictionary directions.
- [Sparse Autoencoders Find Highly Interpretable Features in Language Models](https://arxiv.org/abs/2309.08600) is an early study of sparse autoencoders applied to language-model activations.
- [Towards Monosemanticity: Decomposing Language Models With Dictionary Learning](https://transformer-circuits.pub/2023/monosemantic-features/) explains the motivation for learned sparse features and shows how individual features can be inspected.
- [Qwen-Scope: Turning Sparse Features into Development Tools for Large Language Models](https://arxiv.org/abs/2605.11887) presents the pretrained Qwen sparse autoencoders used in the notebook and studies feature analysis and intervention.
- [Qwen-Scope SAE](https://huggingface.co/collections/Qwen/qwen-scope) contains the downloadable Qwen3 and Qwen3.5 SAE checkpoints, including residual-stream SAEs at different sparsity levels.

### Closely Related Software and Interfaces

- [TransformerLens](https://transformerlensorg.github.io/TransformerLens/) provides standardized activation caching, hook points, and intervention utilities. The lab implements hooks directly in PyTorch for teaching purposes, but TransformerLens is a natural next step for larger experiments.
- [SAELens](https://github.com/decoderesearch/SAELens) supports loading, training, evaluating, and analyzing sparse autoencoders.
- [Neuronpedia](https://www.neuronpedia.org/) provides interactive feature pages with examples, activation views, automated explanations, and steering interfaces for supported model and SAE releases.

## Relevant Papers

### Foundations and Transformer Circuits

- [A Mathematical Framework for Transformer Circuits](https://transformer-circuits.pub/2021/framework/index.html) develops a vocabulary for analyzing transformer computation through residual streams, attention-head circuits, and paths through the model.
- [In-context Learning and Induction Heads](https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html) studies induction heads and their relationship to in-context learning.
- [Interpretability in the Wild: a Circuit for Indirect Object Identification in GPT-2 Small](https://arxiv.org/abs/2211.00593) presents a detailed end-to-end circuit analysis of a natural-language behavior.
- [Toy Models of Superposition](https://transformer-circuits.pub/2022/toy_model/index.html) gives the conceptual motivation for why models may represent more features than they have available dimensions.
- [Towards Automated Circuit Discovery for Mechanistic Interpretability](https://arxiv.org/abs/2304.14997) introduces ACDC, an approach for automatically identifying model components involved in a behavior.
- [Towards Best Practices of Activation Patching in Language Models](https://arxiv.org/abs/2309.16042) explains how corruption methods and evaluation metrics can substantially change activation-patching conclusions.

### Linear Representations and Steering

- [Linguistic Regularities in Continuous Space Word Representations](https://aclanthology.org/N13-1090/) is a very early work on the word-vector arithmetic idea and intuition.
- [The Geometry of Truth: Emergent Linear Structure in Large Language Model Representations](https://arxiv.org/abs/2310.06824) studies linear structure associated with truth and falsehood in model activations.
- [Refusal in Language Models Is Mediated by a Single Direction](https://arxiv.org/abs/2406.11717) demonstrates strong behavioral effects from adding or removing a residual-stream direction associated with refusal.
- [AxBench: Steering LLMs? Even Simple Baselines Outperform Sparse Autoencoders](https://arxiv.org/abs/2501.17148) benchmarks representation-steering methods and is useful for comparing SAE-based methods against simpler baselines.

### Sparse Autoencoders and Feature Discovery

- [Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet](https://transformer-circuits.pub/2024/scaling-monosemanticity/) scales sparse feature extraction to a production-scale language model.
- [Gemma Scope: Open Sparse Autoencoders Everywhere All At Once on Gemma 2](https://arxiv.org/abs/2408.05147) releases SAEs across layers and activation sites for the Gemma 2 family.
- [SAEBench: A Comprehensive Benchmark for Sparse Autoencoders in Language Model Interpretability](https://arxiv.org/abs/2503.09532) evaluates SAEs across several proxy and application-oriented metrics and provides an open comparison suite.

### Transcoders and Feature Circuits

- [Transcoders Find Interpretable LLM Feature Circuits](https://arxiv.org/abs/2406.11944) replaces an MLP's input-output mapping with sparse features, making direct feature interactions easier to analyze.
- [Circuit Tracing: Revealing Computational Graphs in Language Models](https://transformer-circuits.pub/2025/attribution-graphs/methods.html) uses cross-layer transcoders to construct attribution graphs of model computations.
- [On the Biology of a Large Language Model](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) applies attribution-graph methods to behaviors including reasoning, planning, hallucination, and multilingual processing.
- [Circuit-Tracer: A New Library for Finding Feature Circuits](https://aclanthology.org/2025.blackboxnlp-1.14/) describes an open library for constructing and inspecting feature-level attribution graphs.

## Mechanistic Interpretability Libraries

- [NNsight](https://nnsight.net/) provides a tracing interface for inspecting and modifying PyTorch model internals while retaining native model implementations. [NDIF](https://ndif.us/) extends this workflow to remotely hosted large models.
- [pyvene](https://stanfordnlp.github.io/pyvene/) is a general intervention library for PyTorch models, supporting configurable activation interventions, causal abstraction experiments, and trainable interventions.
- [Circuit Tracer](https://github.com/decoderesearch/circuit-tracer) is an open implementation for generating and visualizing feature-level attribution graphs.

The notebooks in this repository use direct PyTorch hooks because exposing the underlying mechanism is useful pedagogically. For larger projects, these libraries reduce repeated infrastructure work and make interventions easier to compose.

## Interactive Tools and Pretrained Features

- [Gemma Scope](https://huggingface.co/google/gemma-scope) provides public Gemma 2 SAE weights for residual-stream, MLP, and attention sites, plus selected transcoders and tutorials.
- [Gemma Scope 2](https://ai.google.dev/gemma/docs/gemma_scope) extends Google's interpretability suite to Gemma 3 with SAEs, transcoders, downloadable weights, and interactive tutorials.

## Courses and Explanatory Resources

- [ARENA](https://github.com/callummcdougall/ARENA_3.0) includes practical mechanistic-interpretability exercises covering TransformerLens, probes, activation patching, circuits, and related methods.
- [TransformerLens main demo](https://transformerlensorg.github.io/TransformerLens/generated/demos/Main_Demo.html) gives a hands-on introduction to activation caching, inspection, and interventions.
- [A Comprehensive Mechanistic Interpretability Explainer and Glossary](https://www.neelnanda.io/mechanistic-interpretability/glossary) is a detailed reference for terminology, intuitions, and common experimental techniques.

## Important Note

This guide was last reviewed in June 2026. Software APIs, model support, and available feature releases may change.
