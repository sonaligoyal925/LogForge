# Log Classification System

## 1. Project Overview

**Project Name**: Log Classification System

This project provides an automated pipeline to classify system and application logs using three different hybrid approaches:

- **Regex-based classification** for simple, well-defined patterns.  
- **BERT-based machine learning classification** for semantic log understanding.  
- **LLM-based classification** (via Groq API) for logs from specific sources requiring deeper contextual reasoning.  

The project exposes a **FastAPI** server for uploading CSV files of logs, classifying them, and returning results in a structured format.

---

## 2. Technologies Used

- **Python**: Core programming language used for implementation.  
- **FastAPI**: Lightweight and efficient web framework for serving the classification API.  
- **Pandas**: For reading, processing, and writing CSV files.  
- **Regex (`re` module)**: For rule-based classification of predictable log patterns.  
- **SentenceTransformers (BERT MiniLM-L6-v2)**: To generate embeddings for semantic log classification.  
- **scikit-learn & joblib**: For training and loading the machine learning classifier model (`log_classifier.joblib`).  
- **Groq API (LLMs)**: For classifying complex logs from `LegacyCRM` or other sources where regex/ML may fail.  
- **dotenv**: For securely managing API keys through environment variables.  

### Rationale:
- Regex ensures fast and lightweight detection of common patterns.  
- BERT embeddings enable semantic log understanding without manually writing patterns.  
- LLMs provide flexibility for edge cases and evolving logs that are harder to capture with rules or ML.  
- FastAPI ensures the project is scalable and can easily integrate into other systems.  

---

## 3. Skills Learned

During the development of this project, the following skills were gained:

- Building **multi-strategy classification pipelines** (Regex + ML + LLM).  
- Using **sentence-transformers** to encode textual data into embeddings.  
- Handling **API integration with Groq LLMs**.  
- Designing and exposing APIs with **FastAPI**.  
- Managing **CSV input/output with Pandas**.  
- Applying **software engineering practices** like modularization, environment variable management, and error handling.  

---

## 4. Setup Instructions

### Prerequisites
1. **Python 3.9+** installed.  
2. Install dependencies:  
   ```bash
   pip install -r requirements.txt
   ```

3. Create a .env file in the root directory: 
    ```bash
    GROQ_API_KEY=your_groq_api_key_here
    ```
4. Run the FastAPI Server: To start the server, use the following command:

    ```bash
    uvicorn server:app --reload
    ```

This will start the API on http://127.0.0.1:8000


## 4. Usage 

Upload a CSV file containing logs to the FastAPI endpoint for classification. Ensure the file has the following columns:

- source
- log_message

The output will be a CSV file with an additional column target_label, which represents the classified label for each log entry.
