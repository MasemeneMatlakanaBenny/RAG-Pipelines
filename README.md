## Simple RAG Pipeline

This is my first RAG pipeline based on the python_introduction.txt file.
The python_introduction.txt file contains the information about Python ,specific use cases of Python and how to get started with it. 
The first step is to install all the requirements in the requirements.txt file.
Then the workflow exists within the jupyter notebook.

The RAG architecture has two main components which are the retriever and generator.
The retriever focuses on performing information lookup to find similar context or semantic meaning,
The generator will generate the responses based on the provided information to respond to the user query.
However it should be noted that the generator are LLMs but now with access to the documents.


----

## Step 1: Indexing
Indexing in RAG is a preprocessing offline step.
Here we preprocess the documents and load it. 
From data science and engineering ,we refer it to as the ingestion phase when building robust data pipelines.
Here we ingest the documents and make sure that they are ready for the workflow.
However we will need an embedding model to transform the queries and text from documents into vectors to capture the semantic meaning.
The need for vectors is also based on ensuring that we have retrieved the correct information based on the cosine similarity metric.
Hence as part of the indexing ,we will generate the vectors from the text we have and store these vectors in a vector database which is Chroma in this case.
Other vector stores such as Pinecone and Weaviate are available.

Vectors goes into the vector stores.

---

## Step 2: Retriever
After the ingestion step,we have the retriever which is a component of the RAG architecture and system that focuses on finding the most relevant information to our queries.
The retriever will search for similar context within the vector database after storing the embedded vectors in it. 
In the retriever ,we also pass metrics that we want to use to evaluate the retrieved information. This is where vectors now come into play.
Lower cosine similariy means that the vectors are closer to each other in the space and higher cosine similarity means context is far from each other.

Retriever takes in the query-> Embedding model turns the query into the vector -> Retriever searches within the vector store for similar context -> 
Cosine similarity between each document chunk and embedded query -> Returns text for vector with lower cosine similarity.


----


