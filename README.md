[README.md](https://github.com/user-attachments/files/21539932/README.md)

#  Agentic RAG System – My Implementation Guide

This README walks you through how to use the Agentic RAG (Retrieval-Augmented Generation) system based on IBM’s official tutorial: [Agentic RAG on IBM Think](https://www.ibm.com/think/tutorials/agentic-rag#763338457). 

---

##  What You Need Before Starting

To get this up and running, here’s what I used:

### 1. IBM Cloud Account
- I signed up here: https://cloud.ibm.com/registration

### 2. Access to IBM watsonx.ai
- Created a new project on watsonx.ai (used a Lite plan to start)
- Grabbed my API key and project ID from the IBM Cloud dashboard

### 3. Python Setup
- I used Python 3.9+ and created a virtual environment to keep things clean
- You can use either `venv` or `conda`

---

## ⚙️ Setting Up the Environment

Here’s what I installed after activating my virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

pip install langchain
pip install langchain-ibm
pip install ibm-watsonx-ai
pip install ibm_watson_machine_learning
pip install chromadb
pip install tiktoken
pip install bs4
pip install python-dotenv
```

---

## Setting Up the .env File

To avoid hardcoding sensitive info, I created a `.env` file in the project root:

```env
WATSONX_APIKEY=your_ibm_watsonx_api_key
PROJECT_ID=your_project_id
```

This is what LangChain and IBM tools use to connect securely.
An input section may also show up when running to input APIKEY and ProjectID.
---

## How It Works – My Build Process

### Step 1: Environment + Setup
- Installed all the packages above
- Loaded environment variables from `.env`

### Step 2: Base Agent Creation
- I started with a minimal agent (no tools or memory yet)

### Step 3: Knowledge Base Integration
- Used ChromaDB to embed, chunk, and index custom data
- This is where the agent starts to “know” things

### Step 4: Tool Registration
- Created and registered tools to access the knowledge base
- These tools are like "helper functions" the agent can call

### Step 5: Prompt Templates
- Used LangChain’s `PromptTemplate` to structure queries
- Helps the agent understand what kind of answers I want

### Step 6: Adding Memory
- Gave the agent a short-term memory buffer
- Used `ConversationBufferMemory` to track interactions

### Step 7: Final Output Loop
- Hooked everything together in a chain (agent + memory + tools)
- System can now take user input → retrieve info → reason → respond

---
Further details on how to run is on the link posted at the top
## What Makes This Powerful

- Agentic RAG doesn’t just retrieve – it **thinks with memory** and **uses tools**
- You can scale this with more complex tools, APIs, or even voice input
- Built on watsonx.ai so the generation quality is enterprise-ready

Nice code. I am curious, if you were ask an opinionated question what would be the outcome?
    For example: "Who performed the worst at the US Open in 2022?"
    I thnk it would probably output "I don't know," or something along the lines of, "There's no way to accutrately tell". 
  - Isaac