# RAG Pipeline Overview

### 1. Ingestion
In this stage, raw documents such as PDFs, text files, or Markdown sources are collected and prepared.  
The goal is to make the data accessible and processible for downstream RAG components.

### 2. Chunking
Documents are split into smaller, manageable pieces called chunks.  
The chosen chunking strategy directly affects retrieval accuracy and contextual relevance.

### 3. Embedding
Each text chunk is transformed into a numerical vector that captures its semantic meaning.  
These embeddings enable semantic similarity search rather than keyword-based matching.

### 4. Indexing
The generated embeddings are stored and organised within a vector database.  
Efficient indexing enables fast, scalable retrieval at query time.

### 5. Retrieval
Given a user query, the system selects the most relevant chunks from the vector store.  
This step determines which pieces of information will ground the final response.

### 6. Augmentation
Retrieved chunks are injected into the model prompt as contextual evidence.  
This allows the language model to condition its generation on explicit, external information.

### 7. Generation
The language model generates the final answer using both the query and the augmented context.  
The output should remain grounded in the retrieved documents rather than model assumptions.
