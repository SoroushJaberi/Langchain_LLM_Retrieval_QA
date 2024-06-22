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
