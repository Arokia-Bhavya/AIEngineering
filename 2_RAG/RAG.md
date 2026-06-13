# RAG

### Retrieval-Augmented Generation
RAG is a technique that combines information retrieval with text generation. Instead of relying solely on what an LLM learned during training, it first fetches relevant documents from an external knowledge source, then passes them to the LLM as context to generate a response.
The flow looks like this:
User Query → Retrieve relevant docs → Feed docs + query to LLM → Get grounded response


| Problem with LLMs | How RAG Fixes It |
|---|---|
| **Hallucinations** | Grounds responses in retrieved documents |
| **Data Security** | Works with private/local data, no need to send sensitive data for retraining |
| **Cost** | Updating a knowledge base is far cheaper than retraining/fine-tuning |
| **Knowledge Cutoff** | Pulls from live or recently updated documents, keeping answers current |

### Working

| RAG Phase | Steps | When it Runs |
|---|---|---|
| **Indexing** (offline) | Load → Chunk → Embed → Store in Vector DB | Once, or when documents update |
| **Retrieval** (online) | Embed Query → Similarity Search → Retrieve → Generate | On every user request |

### Langchain

LangChain is an open-source framework for building applications powered by LLMs.
It is like LEGO for LLM apps — each piece **(loader, splitter, embedder, LLM)** is a block, and LangChain snaps them together into a working pipeline.

### Chunking Strategy

Chunking is the most critical design decision in a RAG pipeline. It determines what information gets
retrieved, how much context the LLM sees, and ultimately the quality of answers generated.

| Strategy|Real World Use Case|
|---|---|
|FixedChunking|a news article for a simple chatbot|
|Hierarchical|HR policy document where full section context is needed|
|Semantic|Medical research paper where topic boundaries matterCustomPython codebase, PDF invoices, markdown wiki pages|


### Docling
A document parser and loader built specifically for AI applications by IBM. Unlike simple text extractors,
Docling parses PDFs and DOCX files while preserving the full document hierarchy : headings, sections,
and tables - then exports to Markdown or JSON for downstream processing.