# Langchain_LLM_Retrieval_QA

## Overview

This project implements a retrieval-based Question Answering (QA) system using the Langchain framework and large language models (LLMs). The system is designed to process and answer questions from a collection of NASA documents by embedding the text into a vector space and retrieving relevant information.

## Features

- **GPU Availability Check**: Utilizes available GPU resources for efficient computation.
- **PDF Document Processing**: Downloads and processes a collection of NASA documents into a suitable format for analysis.
- **Text Embedding**: Embeds the text using the instructor-xl model to represent the documents in a vector space.
- **Vector Database**: Creates a Chroma vector database from the text embeddings to enable efficient retrieval.
- **LLM Pipeline**: Uses the Dolly v2 model for generating answers based on the retrieved text.
- **Retrieval QA Chain**: Sets up a retrieval QA chain to answer questions based on the document embeddings.

## Installation

To get started, ensure you have the required packages installed. You can install them using the following commands:

```sh
pip install accelerate bitsandbytes chromadb langchain InstructorEmbedding
pip install pypdf sentencepiece tiktoken transformers Xformers
pip install -U sentence-transformers langchain-community
```

## Usage

### 1. Check GPU Availability

Start by checking if your system has available GPU resources to ensure efficient computation. The system will list the details of each available GPU, such as name and memory size.

### 2. Download NASA PDFs

Create a directory to store the NASA documents and download the necessary PDFs into this directory. This step prepares the documents that will be used as the corpus for the QA system.

### 3. Load and Process PDF Documents

Load the downloaded PDF documents using Langchain's document loaders. This step converts the PDFs into a format that can be processed further.

### 4. Split Text into Chunks

The text from the loaded documents is split into manageable chunks. This ensures that each chunk contains a manageable amount of text for embedding and retrieval, facilitating efficient processing.

### 5. Embed Text

Embed the text chunks into a vector space using a pre-trained model. This embedding represents the semantic content of the text, making it easier to retrieve relevant information based on a query.

### 6. Create Vector Database

Create a vector database from the text embeddings. This database allows for efficient retrieval of relevant text chunks based on the input query, leveraging the embedded semantic representations.

### 7. Load Model and Setup Pipeline

Load a pre-trained language model and set up a text generation pipeline. This model will be used to generate answers based on the retrieved text chunks from the vector database.

### 8. Setup QA Retrieval Chain

Set up a retrieval QA chain using Langchain's tools. This chain will handle the retrieval of relevant text chunks and generate answers using the language model, ensuring that the answers are based on the embedded document content.

### 9. Query Function

Use the provided query function to interact with the QA system. This function allows you to input a question, retrieves relevant text chunks from the vector database, generates an answer using the language model, and displays the answer along with the sources of the retrieved text.

This usage guide outlines the steps to set up and use your QA system without directly showing the code, making it accessible and easy to follow for users who want to implement the system on their own.



## Models Used

### 1. Instructor-XL Model

The `instructor-xl` model is utilized to embed the text from the documents into a high-dimensional vector space. This embedding represents the semantic content of the text, making it easier to perform efficient and accurate retrievals based on queries.

**Features:**
- **High-Dimensional Embeddings**: Converts text into dense vectors that capture semantic meaning.
- **Device Compatibility**: Can be executed on available GPUs for faster computation.
- **Integration with Langchain**: Seamlessly integrates with Langchain's embedding and vector database components.

### 2. Dolly V2 Model

The `Dolly V2` model, specifically the `databricks/dolly-v2-3b` variant, is used for generating text based on the retrieved document chunks. This model is known for its capability to generate coherent and contextually appropriate responses, making it suitable for question-answering tasks.

**Features:**
- **Text Generation**: Capable of generating high-quality, contextually relevant text responses.
- **Efficient Memory Usage**: Supports loading in 8-bit mode, reducing memory footprint while maintaining performance.
- **Customization**: Parameters like maximum length, temperature, top-p, and repetition penalty can be adjusted to control the response characteristics.

### Pipeline Setup

**Instructor-XL Embeddings:**
- The text from documents is first split into manageable chunks.
- Each chunk is embedded into a vector space using the `instructor-xl` model.
- These embeddings are stored in a Chroma vector database, enabling efficient retrieval.

**Dolly V2 Text Generation:**
- A text generation pipeline is established using the `Dolly V2` model.
- The model and tokenizer are configured to generate responses based on the retrieved text chunks.
- The pipeline ensures that responses are coherent and contextually appropriate for the input queries.

### Combined Workflow

1. **Text Splitting**: The documents are divided into smaller chunks to facilitate processing.
2. **Text Embedding**: The `instructor-xl` model converts these chunks into high-dimensional vectors.
3. **Vector Database**: These embeddings are stored in a vector database for efficient retrieval.
4. **Text Retrieval**: Relevant chunks are retrieved based on the user's query.
5. **Text Generation**: The `Dolly V2` model generates a response based on the retrieved chunks.
6. **Response Presentation**: The generated answer is presented to the user, along with the sources of the information.

This combined use of the `instructor-xl` model for embedding and the `Dolly V2` model for text generation ensures that the QA system can handle complex queries and provide accurate, contextually relevant answers.


## Future Work

### 1. Enhanced Document Processing

- **Support for More Document Formats**: Extend the system to support additional document formats such as DOCX, HTML, and plain text files.
- **Advanced Text Preprocessing**: Implement more sophisticated text preprocessing techniques to handle noise, extract more meaningful information, and improve the quality of embeddings.

### 2. Improved Retrieval Mechanism

- **Hybrid Retrieval**: Combine dense vector-based retrieval with traditional keyword-based retrieval to enhance the accuracy and relevance of the retrieved documents.
- **Dynamic Chunking**: Implement dynamic text chunking techniques that adapt chunk sizes based on the content's structure, ensuring better context preservation.

### 3. Advanced Models

- **Transformer-based Models**: Experiment with more advanced transformer models for embedding and text generation, such as BERT, GPT-3, or T5, which might provide better performance and more accurate answers.
- **Multilingual Support**: Incorporate multilingual models to support question-answering in multiple languages, expanding the system's applicability.

### 4. Real-Time QA System

- **Live Document Update**: Implement a mechanism to update the document database in real-time, ensuring that the system can handle dynamic and frequently changing information.
- **Streaming Queries**: Develop the ability to handle streaming queries, providing answers in real-time as users input their questions.

### 5. Enhanced User Interaction

- **Interactive Interface**: Create an interactive user interface with visualization tools to help users explore the documents and understand the retrieval process.
- **Voice Input and Output**: Integrate voice input and output capabilities to make the system more accessible and user-friendly.

### 6. Better Evaluation Metrics

- **Performance Metrics**: Implement more sophisticated evaluation metrics to measure the accuracy, relevance, and user satisfaction of the answers provided by the system.
- **User Feedback Loop**: Develop a feedback loop where users can rate the answers, and use this feedback to continuously improve the system's performance.

## Potential Better Models for Future Use

### 1. GPT-4

- **Capabilities**: GPT-4 offers superior language understanding and generation capabilities, making it an excellent choice for both embedding and text generation tasks.
- **Performance**: With more parameters and advanced training techniques, GPT-4 can provide more accurate and contextually relevant answers.

### 2. BERT (Bidirectional Encoder Representations from Transformers)

- **Capabilities**: BERT excels at understanding the context within text due to its bidirectional nature, making it ideal for embedding tasks.
- **Variants**: Consider using variants like RoBERTa or DistilBERT for specific tasks or for reducing computational requirements.

### 3. T5 (Text-To-Text Transfer Transformer)

- **Capabilities**: T5 is a versatile model that can handle a wide range of NLP tasks by converting them into a text-to-text format, making it highly adaptable for both embedding and generation.
- **Efficiency**: T5's efficiency and performance can be leveraged for more complex and nuanced QA systems.

### 4. Dense Passage Retrieval (DPR)

- **Capabilities**: DPR provides an efficient way to retrieve passages from a large corpus using dense vectors, significantly improving retrieval performance.
- **Integration**: Integrating DPR with advanced language models can enhance both the retrieval and answer generation stages.

### 5. Multilingual Models

- **Capabilities**: Models like mBERT or XLM-Roberta are designed to handle multiple languages, making them suitable for developing a multilingual QA system.
- **Applicability**: These models can be used to expand the system's functionality to support a wider range of languages and cultural contexts.

By implementing these future work suggestions and leveraging advanced models, you can significantly enhance the performance, usability, and applicability of your retrieval-based QA system.
