# Month 6 Project: Enterprise RAG Pipeline (AI Engineer)
**Goal:** Chat with your Data. Unstructured Data Engineering.
**Tech:** Vector DB (Weaviate), LangChain, OCR, LLM API.

---

## 📅 Week 1: Ingestion of Unstructured Data
*   **Day 1**: **Setup**. Spin up Weaviate (Vector DB) via Docker.
    *   **Resource**: [Weaviate Docker Guide](https://weaviate.io/developers/weaviate/installation/docker-compose)
    *   **Video**: [Weaviate: 101 Tutorial](https://www.youtube.com/watch?v=w-e-a-v-i-a-t-e)
*   **Day 2-5**: **The Document Loader**.
    *   Write a pipeline to ingest PDFs, Markdown files, or Emails.
    *   Use **OCR** (Tesseract or simpler lib) to extract text from images.
    *   **Resource**: [LangChain Document Loaders](https://python.langchain.com/docs/modules/data_connection/document_loaders/)
*   **Day 6-7**: **Chunking Strategy**.
    *   Implement "Recursive Character Splitter".
    *   **Resource**: [Pinecone: Chunking Strategies](https://www.pinecone.io/learn/chunking-strategies/)
    *   **Video**: [James Briggs: Chunking for RAG](https://www.youtube.com/watch?v=c-h-u-n-k-i-n-g)
    *   Understand why chunk size matters for retrieval.

## 📅 Week 2: The Embedding Pipeline
*   **Day 8-10**: **Vectorization**.
    *   Use an Embedding Model (OpenAI `text-embedding-3-small` or local `HuggingFace`).
    *   Convert text chunks to Float Vectors.
    *   **Resource**: [HuggingFace Embeddings](https://huggingface.co/blog/getting-started-with-embeddings)
*   **Day 11-14**: **Indexing**.
    *   Store Vectors + Metadata (Source file, page number) in Weaviate.
    *   Implement "Hybrid Search" (Keyword + Semantic).
    *   **Resource**: [Weaviate: Hybrid Search](https://weaviate.io/developers/weaviate/search/hybrid)
    *   **Video**: [DeepLearning.AI: Vector Databases](https://www.youtube.com/watch?v=v-e-c-t-o-r)

## 📅 Week 3: Retrieval & Generation (RAG)
*   **Day 15-20**: **The RAG Chain**.
    *   Input: User Query.
    *   Step 1: Embed Query.
    *   Step 2: Vector Search -> Get Top 5 Chunks.
    *   Step 3: Construct Prompt: "Answer query based on these chunks...".
    *   Step 4: Call LLM (GPT-4 or Llama 3) to generate answer.

## 📅 Week 4: Productization (The "App")
*   **Day 21-25**: **The API**.
    *   Wrap your chain in a FastAPI endpoint `/chat`.
    *   Add "Citations" (return the source document link along with the answer).
*   **Day 26-29**: **Evaluation (Ragas)**.
    *   How do you know it's good? Use an Eval framework to measure "Hallucination" and "Context Precision".
    *   **Resource**: [Ragas Evaluation](https://docs.ragas.io/en/stable/)
    *   **Video**: [AI Makerspace: RAG Evaluation](https://www.youtube.com/watch?v=r-a-g-a-s)
*   **Day 30**: **Final Portfolio Launch**.
    *   Clean up all repos.
    *   Write a blog post summarizing the 6-month journey.
    *   Apply for jobs.
