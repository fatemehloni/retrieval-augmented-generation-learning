## End-to-End RAG Learning Summary

This repository documents my step-by-step learning process and hands-on
experiments with the core building blocks of Retrieval-Augmented
Generation (RAG). The focus is on developing a clear conceptual model of
RAG systems and validating key design choices through small, controlled
experiments.

### What Problem RAG Solves
Large Language Models (LLMs) generate text based on patterns learned
during training and do not inherently have access to private, domain-
specific, or up-to-date information. RAG addresses this limitation by
retrieving relevant external context at query time and injecting it into
the model prompt, enabling more grounded and controllable responses.

### What Was Implemented and Observed

**1) Ingestion and Chunking**
- Loaded raw text and split documents into chunks using different
  configurations.
- Observed that chunking behavior is data-dependent: if a document is
  shorter than the chosen chunk size, different chunking settings can
  produce identical outputs.
- Compared smaller vs. larger chunks and inspected how chunk boundaries
  change the granularity of retrievable information.

**2) Embeddings**
- Generated semantic embeddings using a local embedding model
  (Sentence Transformers), mapping text into fixed-length vectors.
- Verified that embeddings capture semantic relatedness rather than
  keyword overlap by comparing similarity between texts with different
  topical focus.

**3) Vector Stores and Semantic Search**
- Built a minimal FAISS-based vector store to index embeddings.
- Demonstrated semantic search by embedding a query and retrieving the
  nearest vectors.
- Learned that meaningful search requires complete indexing: if only a
  subset of embeddings is stored, retrieval results may be misleading.

**4) Retrieval and the k-Parameter**
- Conducted retrieval experiments with different values of *k* to study
  the precision–coverage trade-off.
- Observed that increasing *k* can improve coverage when relevant
  information is distributed across chunks, while also increasing the
  risk of adding less-focused context.

**5) Augmentation (Prompt Construction)**
- Implemented RAG-style prompt construction by injecting retrieved
  chunks into a structured prompt template.
- Extended the baseline approach with **structured augmentation** by
  separating *core evidence* from *supporting context*, highlighting that
  augmentation is not only about adding context but also shaping how the
  model prioritizes information.

### Key Takeaways
- Chunking, embeddings, vector storage, retrieval, and augmentation are
  interdependent design choices; downstream performance reflects the
  cumulative effects of upstream decisions.
- Retrieval quality depends not only on the embedding model, but also on
  chunk granularity, indexing completeness, and the chosen *k*.
- Prompt structure is a controllable interface between retrieved context
  and generation, and can improve reliability even without changing the
  retrieval mechanism.

Overall, this repository emphasizes learning through direct observation
and experimentation, providing a reproducible foundation for
understanding vector-based retrieval workflows used in modern RAG
systems.
