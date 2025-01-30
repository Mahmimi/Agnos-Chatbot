# Agnos Healthcare Chatbot

This project is an interview test assignment for Agnos company. It involves building a Retrieval-Augmented Generation (RAG) chatbot designed to provide responses based on scraped healthcare forum data.


## Hugging Face Space

The chatbot uses the `gradio` library for developing chat UI. You can find it here:

🔗 [Hugging Face Space](https://huggingface.co/spaces/Jiranuwat/AgnosChatbot)

![Hugging Face Capture](images\Chatbot_Banner.PNG)

---

## Project Overview

The chatbot consists of two main pipelines:



## 1. Data Collection from Web Scraping

The first pipeline involves gathering data from the **Agnos healthcare forum**, processing it, and storing embeddings in a vector database.

### Steps:
1. **Web Data:** Scrape data from the Agnos forum (174 pages, 1390 articles).
2. **Web Crawler:** Use `Selenium` and `BeautifulSoup` to extract relevant information.
3. **CSV Storage:** Store extracted data in a structured format.
4. **LLM Model Encoding:** Use the `paraphrase-multilingual-mpnet-base-v2` model (Thai supported) to generate text embeddings.
5. **Vector Store:** Store embeddings in **Qdrant**, an open-source vector database for efficient similarity search.

### Pipeline Diagram:
![Data Collection Pipeline](images\pipeline1.PNG)

---

## 2. Implementation Pipeline

This pipeline handles user interactions and generates responses based on vector search and GPT API.

### Steps:
1. **User Input:** Receive a query from the user.
2. **LLM Model Encoding:** Convert the input into an embedding using `paraphrase-multilingual-mpnet-base-v2`.
3. **Standalone Question Generation:** Create a refined question representation.
4. **Vector Store Search:** Perform a **two-stage similarity search** in Qdrant to retrieve relevant context combined with **reranking** using BM25.
5. **Engineered Prompt:** Format retrieved context and user query into a structured prompt.
6. **GPT API Query:** Send the prompt to the GPT model for a response.
7. **Conversation:** Display the chatbot’s response.

### Pipeline Diagram:
![Implementation Pipeline](images\pipeline2.PNG)

---

## ⚠️ Critical Notice

**Do not attempt to re-run any script without setting up the necessary API keys!**  
This repository does **not** include any API credentials for web scraping, GPT API access, or Qdrant database connections. You must configure your own credentials before execution.
