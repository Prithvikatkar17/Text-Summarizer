# Text Summarizer

A web application that leverages the power of HuggingFace's T5 Transformer model to generate concise summaries of text or dialogue. The backend is built with FastAPI, providing both a user-friendly UI and a REST API endpoint.

## Features

- **T5 Transformer Model**: Uses a pre-trained T5 model for high-quality conditional text generation.
- **FastAPI Backend**: Fast and asynchronous backend to handle summarization requests.
- **Modern UI**: A clean, responsive, and easy-to-use web interface for quick summarization.
- **REST API**: Accessible `/summarize/` endpoint for programmatic integration.
- **Hardware Acceleration**: Automatically detects and uses GPU (CUDA/MPS) if available, otherwise falls back to CPU.

## Tech Stack

- **Backend**: Python, FastAPI, Uvicorn
- **Machine Learning**: PyTorch, HuggingFace Transformers (`T5ForConditionalGeneration`, `T5Tokenizer`)
- **Frontend**: HTML, CSS, JavaScript, Jinja2 Templates

## Setup & Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Prithvikatkar17/Text-Summarizer.git
   cd Text-Summarizer
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv env
   # Windows:
   .\env\Scripts\activate
   # Linux/Mac:
   source env/bin/activate
   ```

3. **Install dependencies:**
   Make sure to install the required libraries (you may want to add a `requirements.txt` file):
   ```bash
   pip install fastapi uvicorn torch transformers pydantic jinja2
   ```
   *Note: Install the appropriate version of PyTorch for your system (CUDA/MPS).*

4. **Model Setup:**
   The application expects the T5 model and tokenizer to be saved in a `./saved_model` directory. If you haven't trained your own model, you can download a pre-trained model (like `t5-small`) using a quick Python script:

   ```python
   from transformers import T5ForConditionalGeneration, T5Tokenizer
   
   model_name = "t5-small"
   model = T5ForConditionalGeneration.from_pretrained(model_name)
   tokenizer = T5Tokenizer.from_pretrained(model_name)
   
   model.save_pretrained("./saved_model")
   tokenizer.save_pretrained("./saved_model")
   ```
   Run this code once to populate the `./saved_model` directory before starting the application.

## Usage

Start the FastAPI application using Uvicorn:

```bash
uvicorn app:app --reload
```

- Open your browser and navigate to `http://127.0.0.1:8000` to access the web UI.
- Enter your text in the text area and click **Summarize**.

## API Documentation

You can also use the `/summarize/` POST endpoint directly:

**Endpoint:** `/summarize/`  
**Method:** `POST`  
**Payload:**
```json
{
  "dialogue": "Your long text goes here..."
}
```

**Response:**
```json
{
  "summary": "Your generated summary."
}
```

FastAPI automatically generates interactive API documentation. You can view it by navigating to:
- Swagger UI: `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

- <img width="2880" height="1630" alt="Screenshot 2026-10-02 110326" src="https://github.com/user-attachments/assets/38b47345-286b-4eba-b4d9-8b07b55576cc" />
<img width="2880" height="1626" alt="Screenshot 2026-10-02 110454" src="https://github.com/user-attachments/assets/e339914c-2518-4fd0-a7a8-e1cf584ef1e4" />
<img width="2880" height="1628" alt="Screenshot 2026-10-02 110556" src="https://github.com/user-attachments/assets/bce67894-c7fc-43d2-9507-26bceaedaf4a" />


