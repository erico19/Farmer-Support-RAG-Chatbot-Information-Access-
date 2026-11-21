<div align="center">
  <img src="https://cdn-icons-png.flaticon.com/512/2909/2909763.png" width="120" height="120" alt="AgriRAG Logo"/>
</div>

# AgriRAG Assistant

AgriRAG is an Artificial Intelligence application based on Retrieval-Augmented Generation (RAG). It is designed to provide highly contextualized answers to agricultural questions by leveraging a local document database tailored to local soils, crops, and climate conditions in Uganda and East Africa.

## 🚀 Objectives

- Facilitate access to accurate agricultural information for smallholder farmers and agripreneurs.
- Exploit local documents (technical guides, PDFs, research reports) to answer specific farming questions without AI hallucinations.
- Deploy an accessible AI agent online (via Streamlit or Hugging Face Spaces) to empower agricultural extension workers.


🚀 How to Setup on Local PC & Run the Application
Follow these steps to set up and run the AgriRAG application on your local machine.

Prerequisites
Python 3.9+ installed on your machine.

An OpenAI API Key or a Hugging Face Token (depending on the LLM backend you choose to configure).

Git installed on your computer.

Step 1: Clone the repository
Open your terminal or command prompt and run:


bash
git clone (https://github.com/erico19/Farmer-Support-RAG-Chatbot-Information-Access-/tree/main)
cd AgriRAG

Step 2: Create a Virtual Environment (Recommended)
It is best practice to run this in a virtual environment to avoid dependency conflicts.

bash
# For Windows:
python -m venv venv
venv\Scripts\activate

# For Mac/Linux:
python3 -m venv venv
source venv/bin/activate
Step 3: Install dependencies
Install all the required Python libraries:

bash
pip install -r requirements.txt
Step 4: Set up your API Key
Create a file named .env in the root directory of the project. Open it in a text editor (like Notepad or VS Code) and add your API key:

text
# If using OpenAI:
OPENAI_API_KEY=your_openai_api_key_here

# If using Hugging Face:
HUGGINGFACEHUB_API_TOKEN=your_huggingface_token_here
(Note: Do not share this .env file on GitHub. Add .env to your .gitignore file).

Step 5: Add your agricultural documents
To make the RAG app work, it needs data. Place your PDFs, Word documents, or text files (e.g., Maize_Farming_Guide.pdf, Coffee_Diseases.docx) inside the data/documents/ folder.

Step 6: Run the application
Start the Streamlit app:

bash
streamlit run app/main.py
Step 7: Access the Interface
Once the app starts, it will provide a local URL in your terminal. Open your web browser and go to:

text
http://localhost:8501
📄 License
This project is licensed under the MIT License. Created by Mafabi Eric.


## 🏗️ Project Architecture

```mermaid
graph LR
    subgraph Frontend
        A[Streamlit UI] --> B[main.py]
    end

    subgraph Backend
        B --> C[Retriever FAISS/ChromaDB]
        D[Local Documents .pdf, .docx] --> C
        B --> E[LLM via OpenAI / HuggingFace]
        E --> F[Augmented Response]
    end

    subgraph "Data Pipeline"
        J[Data Ingestion] -- Chunking & Embedding --> K[Vector Store]
        K -- Semantic Search --> D
    end

    subgraph Deployment
        G[GitHub] --> H[CI/CD]
        H --> I[Streamlit Cloud / Hugging Face]
    end
