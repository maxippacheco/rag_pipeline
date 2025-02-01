# RAG Pipeline

This is a RAG pipeline that consists in three principal components:
- Data Embedding and Storage Component.
- Data Embedding and Storage Component.
- Augmented Input Generation Component.

Components explanation:

## Data Collection and Preparation Component

This component is responsible for collecting and preparing data for use in the larger pipeline.

### Functionality

1. **Data Collection:** It fetches articles from a list of Wikipedia URLs related to space exploration.
2. **Data Cleaning:** It cleans the raw text by removing references, citations, unwanted characters, and extra whitespaces.
3. **Data Storage:** It stores the cleaned text in a file named `llm.txt`.

## Data Embedding and Storage Component

### Description

This component is responsible for embedding the source text data and storing it in a Deep Lake vector store. It performs the following steps:

1. **Data Loading:** Reads the source text file (`llm.txt`).
2. **Chunking:** Splits the text into smaller chunks of a defined size (CHUNK_SIZE).
3. **Embedding:** Uses OpenAI's text-embedding-ada-002 model to generate embeddings for each text chunk.
4. **Storage:** Creates a Deep Lake vector store and stores the text chunks, embeddings, and metadata (source file).

## Augmented Input Generation Component

This component is responsible for augmenting user input with relevant information retrieved from a vector store before feeding it to a large language model (LLM). This process enhances the LLM's understanding and helps it generate more comprehensive and accurate responses.

### Functionality

1. **Retrieves User Input:** Obtains the initial query or prompt from the user.
2. **Searches Vector Store:** Uses the user input to search a pre-built vector store containing relevant information.
3. **Selects Top Result:** Identifies the most relevant document from the search results based on a similarity score.
4. **Augments User Input:** Combines the original user input with the selected document's content to create an augmented input.
5. **Feeds Augmented Input to LLM:** Passes the augmented input to a large language model (e.g., GPT-4) for further processing and response generation.
6. **Evaluates Response:** Assesses the quality and relevance of the LLM's response using cosine similarity or other metrics.

