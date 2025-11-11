# Agentic RAG with LangGraph

This repository builds a conversational agent that can answer questions from recent news articles. We start with a template agent in `langchain_tutorial.ipynb` from the LangChain [docs](https://docs.langchain.com/oss/python/langchain/rag). 

Then, we build an agent in `pinecone_rag.ipynb` as follows:
1. Collect recent news articles from AP News and Reuters.
2. Build a vector DB with Pinecone and OpenAI embeddings.
3. Define an agent with LangGraph that iteratively retrieves documents and refines the question based on available information (see figure below).
4. Answer the refined question.

The LangGraph agent flow can be seen here:
<img width="643" height="692" alt="agent_flow" src="https://github.com/user-attachments/assets/43e07865-79d1-4979-963e-9ddecbb6d42b" />
