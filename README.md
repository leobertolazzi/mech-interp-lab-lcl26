# Mechanistic Interpretability Lab @ Lectures on Computational Linguistics 2026

This repository contains the materials for the *"Mechanistic Interpretability Lab"* held by [Leonardo Bertolazzi](https://leobertolazzi.github.io/) at the [AILC Lectures on Computational Linguistics 2026](https://www.ai-lc.it/en/lectures-2/lectures-2026/).

## Overview

Large Language Models can often be controlled by changing their prompts or through fine-tuning, but this gives us little insight into how the requested behavior is represented or produced internally. The problem we will focus on in this lab is therefore:

> How can we locate a concept inside a language model and intervene on it in a way that is both effective and interpretable?

We study this question through a deliberately simple behavior: controlling whether a model answers in English or Italian. Language is easy to recognize in generated text, giving us a clear setting in which to connect model behavior with its internal activations.

The lab progressively moves from external control toward more interpretable internal interventions:

1. **Prompting:** we first control the output language through prompts, treating the model as a black box.
2. **Residual-stream analysis:** we record internal activations and use layer-wise PCA to inspect where English and Italian examples become distinguishable.
3. **Steering vectors:** we represent the Italian language as a difference-in-means direction and add or subtract it during generation.
4. **Sparse Autoencoders:** we decompose residual activations into sparse learned features, identify features associated with Italian text, and intervene using their decoder directions.

## Content

The lab is based on the following two notebooks:

- [Notebook 01 - Prompting and Steering Vectors](01_prompting_and_steering_vectors.ipynb) starts with prompt-based black-box control, scans all residual-stream layers with 2D PCA, then finds and applies contrastive steering vectors at selected layers to activate or suppress Italian.
- [Notebook 02 - Sparse Autoencoders](02_sparse_autoencoders.ipynb) decomposes layer-4 residual-stream activations with a Sparse Autoencoder and uses sparse Italian-language features for analysis and intervention.

## Optional Language Extension

The lab focuses on Italian as the non-English language. For optional experimentation, the repository provides the same data, in the same order, for:

- German
- Spanish
- Chinese
- Turkish

Each language has three files in `data/`:

```text
<language>_sentences.json
<language>_test_questions.json
<language>_unseen_sentences.json
```

To repeat the experiment with another language, replace the Italian data loaded in the notebooks with the corresponding files and update the language-specific prompts, marker-word classifier, labels, and plot text. The conceptual procedure is unchanged: contrast English with the chosen language, discover the corresponding residual or SAE directions, and test whether adding or subtracting them controls generation.

## Running in Colab

The notebooks in this lab are intended to be used mainly via [Google Colab](https://colab.research.google.com/). You can open them directly here:

- [Notebook 01 - Prompting and Steering Vectors](https://colab.research.google.com/github/leobertolazzi/mech-interp-lab-lcl26/blob/main/01_prompting_and_steering_vectors.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/leobertolazzi/mech-interp-lab-lcl26/blob/main/01_prompting_and_steering_vectors.ipynb)
- [Notebook 02 - Sparse Autoencoders](https://colab.research.google.com/github/leobertolazzi/mech-interp-lab-lcl26/blob/main/02_sparse_autoencoders.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/leobertolazzi/mech-interp-lab-lcl26/blob/main/02_sparse_autoencoders.ipynb)

Before starting, set a GPU runtime:

```text
Runtime -> Change runtime type -> T4 GPU
```

## Local Setup

Colab is the preferred environment. However, you can also clone this repository and run the notebooks locally. GPU execution is recommended.

This project was developed using Python 3.12. We recommend using the same Python version when running the notebooks locally.

### Environment setup

Here is an example of how to create a new Python 3.12 environment and install dependencies using `conda`:

```shell
conda create -n <name> python=3.12 -y
conda activate <name>
pip install -r requirements.txt
```

Alternatively, you can create a virtual environment and install dependencies by running:

```shell
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Running notebooks locally

After installing the dependencies, you can start Jupyter from the command line:

```shell
jupyter notebook
```

or:

```shell
jupyter lab
```

Then open the notebook files from your browser.

Alternatively, you can open and run the notebooks directly in an IDE that supports Jupyter notebooks, such as Visual Studio Code with the Jupyter extension installed. 

Make sure the IDE is using the Python environment you created above.

## Further Reading and Tools

A curated list of papers, libraries, and learning resources is available in [Further Reading and Tools](FURTHER_READING.md).
