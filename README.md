# Customer-support-workflow-using-n8n

This repository contains an automated **Customer Support Email Workflow** built with [n8n](https://n8n.io). It uses Gmail, OpenAI, LangChain, and Pinecone to read incoming support emails, classify them, and generate intelligent responses based on a knowledge base.

---

## workflow Overview

This n8n workflow automates the customer support email handling process using the following steps:

1. **Trigger on New Email (Gmail Trigger)**
   - Listens for new incoming emails in Gmail every minute.

2. **Classify Email (LangChain Text Classifier)**
   - Uses AI to categorize the email as either "Customer Support" or "Other" based on content.

3. **AI Response Generation (LangChain Agent + OpenAI)**
   - If the email is support-related:
     - Retrieves relevant information from a **Pinecone vector store** (FAQ/Policy).
     - Generates a response using **OpenAI GPT-4.1**, customized with a professional support prompt.
   - If not support-related:
     - Performs no operation.

4. **Send Response (Gmail Node)**
   - Automatically replies to the customer using the AI-generated response.

