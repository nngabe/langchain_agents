# Agentic RAG with LangGraph

This repository builds a conversational agent that can answer questions from recent news articles. We start with a template agent in `langchain_tutorial.ipynb` from the LangChain [docs](https://docs.langchain.com/oss/python/langchain/rag). 

We then build an agent in `pinecone_rag.ipynb` as follows:
1. Collect recent news articles from AP News and Reuters.
2. Build a vector DB with Pinecone and OpenAI embeddings.
3. Define an agent with LangGraph that iteratively retrieves documents and refines the question based on available information (see figure below).
4. Answer the refined question.

The LangGraph agent flow can be seen here:

<img width="420" height="520" alt="agent_flow" src="https://github.com/user-attachments/assets/43e07865-79d1-4979-963e-9ddecbb6d42b" />

## Sample Q&A outputs
Here are some sample Q&A results. See more details of the LangGraph output at the bottom of `pinecone_rag.ipynb`:

```
Query: "what is happening with the government shutdown?"

Update from node generate_query_or_respond
================================== Ai Message ==================================
Tool Calls:
  retrieve_news_articles (call_B0B6H7xZMrxFC3VYqgNpB6Wd)
 Call ID: call_B0B6H7xZMrxFC3VYqgNpB6Wd
  Args:
    query: government shutdown *** REFINED QUERY ***

Update from node retrieve
================================= Tool Message =================================
Name: retrieve_news_articles

X LinkedIn Bluesky Flipboard Pinterest Reddit WASHINGTON (AP) — Talks intensified Tuesday toward a potential end to the government shutdown, as the federal closure was on track to become the longest ever, disrupting the lives of millions of Americans...

contours of an agreement began to emerge. The agreement includes bipartisan bills worked out by the Senate Appropriations Committee to fund parts of government — food aid, veterans programs and the legislative branch, among other things...

...

Update from node generate_answer
================================== Ai Message ==================================

The government shutdown is currently the longest in history, affecting millions of
Americans, with federal employees furloughed or working without pay and disruptions
in services like SNAP benefits and air travel. Bipartisan negotiations areunderway
in the Senate to reach a deal that would reopen the government and address expiring
health insurance subsidies. However, there is tension between parties, with Democrats
criticizing the proposed deal for not adequately addressing healthcare costs.
```

```
Query: "what is happening with the market?"

Update from node generate_query_or_respond
================================== Ai Message ==================================
Tool Calls:
  retrieve_news_articles (call_Qx4PIysbaIUOJrkWtVd5RT6n)
 Call ID: call_Qx4PIysbaIUOJrkWtVd5RT6n
  Args:
    query: stock market news



Update from node retrieve
================================= Tool Message =================================
Name: retrieve_news_articles

More news

X LinkedIn Bluesky Flipboard Pinterest Reddit NEW YORK (AP) — Big Tech and other superstars of the U.S. stock market got back to rallying on Monday, and Wall Street recovered most of its loss from last week.The S&P 500 climbed 1.5%...

That has analysts’ expectations for earnings in 2026 nearly all the way back to where they were before Trump shocked financial markets in April with his “Liberation Day” announcement of worldwide tariffs. All told, the S&P 500 rose 103.63 points to 6,832.43...


Update from node generate_answer
================================== Ai Message ==================================

The U.S. stock market is experiencing a rebound, with major indices like the S&P
500, Dow Jones Industrial Average, and Nasdaq composite all showing significant gains.
Big Tech and AI-related stocks, particularly Nvidia, have been key drivers of this
rally. Additionally, many companies in the S&P 500 have reported stronger-than-expected
profits, contributing to the market's positive momentum.
```
