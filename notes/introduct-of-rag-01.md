# What is Retrieval-Augmented Generation (RAG)?

Large Language Models (LLMs) generate responses based on patterns learned
during training. As a result, their knowledge is limited to the data
available at training time and does not include access to private,
up-to-date, or domain-specific information.

This limitation leads to several challenges:
- Outdated knowledge when recent information is required
- Lack of access to proprietary or internal documents
- Hallucinated responses when the model lacks sufficient grounding

Retrieval-Augmented Generation (RAG) addresses these challenges by
retrieving relevant external documents at query time and injecting them
into the model's context. Instead of relying solely on its internal
parameters, the LLM conditions its generation on retrieved evidence.

At a high level, a RAG system consists of:
1. A document ingestion and indexing pipeline
2. A retrieval mechanism to select relevant context
3. A generation step that produces answers grounded in retrieved content

By separating knowledge storage from language generation, RAG enables
more up-to-date, controllable, and transparent AI systems.

## Example: Why RAG is Needed

Consider a language model that is asked the following question:

> "What changes were introduced in the 2024 version of a company's internal payment API?"

A standalone LLM cannot answer this question reliably because:
- The information is not part of its training data
- The API documentation is private and inaccessible to the model
- The model may generate a plausible but incorrect response (hallucination)

In a RAG-based system, the process is different:
1. The system retrieves relevant internal API documents
2. These documents are injected into the prompt as contextual evidence
3. The LLM generates an answer grounded in the retrieved content

As a result, the response is based on explicit, verifiable sources rather
than the model's internal assumptions.
