**Hallucination-Resistant LLM with RAG**

This project implements a Retrieval-Augmented Generation (RAG) pipeline on top of a GPT-based large language model, designed to reduce hallucinations by grounding answers in a curated knowledge base.

For demonstration, the model uses context from *Avengers: Endgame*. It will:

Give fact-based answers only when the relevant context is found.

Reply with "I don't know" when the answer isn’t in the knowledge base.

Evaluate performance by tracking correct vs. incorrect answers.

##Features
**RAG pipeline** for accurate context retrieval.

**Hallucination prevention** by limiting responses to verified data.

Built-in **accuracy scoring** for model evaluation.

**Domain-specific QA** using Avengers: Endgame as the source material.

##Tech Stack
GPT-based LLM

Retrieval-Augmented Generation (RAG)

Custom evaluation metrics in Python

##Example
Q: Who sacrificed themselves to get the Soul Stone?
A: Black Widow.

Q: Who won the 1998 FIFA World Cup?
A: I don't know.

##License
MIT License
