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
