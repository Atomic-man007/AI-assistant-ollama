# AI-assistant-ollama

## Project Description

This project demonstrates how to use various components from the `langchain_community` and `langchain_core` libraries to load, transform, embed, and retrieve documents from a PostgreSQL database with PGVector enabled. The documents are sourced from URLs, transformed into text, split into manageable chunks, and stored as vectors in the database for retrieval. The project also showcases how to create a RAG (Retrieval-Augmented Generation) chain using the Ollama language model to answer questions based on the context retrieved from the vector store.

## Prerequisites

- Python 3.7+
- PostgreSQL with PGVector enabled
- Docker (optional, for running PostgreSQL with PGVector)

## Installation

1. Clone the repository:

```bash
git clone https://github.com/Atomic-man007/AI-assistant-ollama.git
```

2. Create a virtual environment and activate it:

```bash
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

3. Install the required packages:

```bash
pip install -r requirements.txt
```

4. Set up PostgreSQL with PGVector enabled. You can use Docker to quickly spin up a PostgreSQL instance with PGVector:

```bash
docker run --name pgvector -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 ankane/pgvector
```

5. Set the `DB_URL` environment variable to point to your PostgreSQL instance:

```bash
export DB_URL=postgresql://postgres:mysecretpassword@localhost:5432/postgres
```

## Usage

1. Update the `urls` list in the `main` function with the URLs of the documents you want to process.

2. Run the script:

```bash
python main.py
```

## Components

- **AsyncHtmlLoader**: Asynchronously loads HTML content from the provided URLs.
- **Html2TextTransformer**: Transforms HTML documents into plain text.
- **OllamaEmbeddings**: Embeds the text documents into vector space.
- **PGVector**: A vector store implementation using PostgreSQL with PGVector extension.
- **RecursiveCharacterTextSplitter**: Splits text documents into chunks of specified size.
- **ChatPromptTemplate**: Creates a chat prompt template for generating responses.
- **RunnablePassthrough**: A passthrough runnable for chaining components.
- **Ollama**: A language model used to generate answers based on retrieved context.

## Example

The script demonstrates the following steps:

1. Load HTML documents from the provided URLs.
2. Transform HTML documents into plain text.
3. Split the text documents into smaller chunks.
4. Embed the text chunks into vector space and store them in the PostgreSQL database.
5. Retrieve relevant context from the vector store.
6. Use the retrieved context to generate a response to a question using the Ollama language model.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- `langchain_community` and `langchain_core` libraries for providing the components used in this project.
- PostgreSQL and PGVector for the vector store implementation.
- Ollama for the language model used for generating responses.
