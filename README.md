# Text Summarizer using T5 and FastAPI

A web-based **Text Summarization application** built using **FastAPI** and a fine-tuned **T5 Transformer model** from Hugging Face.

The application allows users to enter or paste a dialogue/text and generate a concise summary through a simple web interface.

## Features

- Text/dialogue summarization
- Fine-tuned T5 model
- Hugging Face Transformers integration
- FastAPI backend
- Simple and responsive HTML interface
- CUDA/GPU support when available
- Automatic fallback to CPU
- REST API endpoint for summarization
- Input text cleaning before summarization

## Project Structure

```text
Text-Summarizer/
│
├── app.py
├── index.html
├── requirements.txt
├── README.md
├── .gitignore
│
└── saved_summary_model/
    ├── model files
    ├── tokenizer files
    └── configuration files
```

## Technologies Used

- Python
- FastAPI
- Hugging Face Transformers
- T5
- PyTorch
- HTML
- CSS
- JavaScript
- Jinja2

## How It Works

The application follows this flow:

```text
User enters dialogue/text
          ↓
      index.html
          ↓
   POST /summarize/
          ↓
       FastAPI
          ↓
    Clean input text
          ↓
      T5 Tokenizer
          ↓
   Fine-tuned T5 Model
          ↓
      Generated Summary
          ↓
       Web Interface
```

## Backend

The backend is implemented using FastAPI.

The application loads the locally saved T5 model and tokenizer from:

```text
./saved_summary_model
```

The model uses CUDA when a compatible GPU is available and otherwise runs on the CPU.

## API Endpoint

### POST `/summarize/`

The endpoint accepts JSON containing the dialogue.

Example request:

```json
{
    "dialogue": "Speaker 1: Hello. Speaker 2: Hi, how are you?"
}
```

Example response:

```json
{
    "summary": "The speakers greet each other and discuss how they are doing."
}
```

## Frontend

The frontend is implemented in `index.html`.

Users can:

1. Enter or paste content.
2. Click the **Summarize** button.
3. Wait while the model processes the input.
4. View the generated summary.

The frontend communicates with the FastAPI backend using JavaScript and the `/summarize/` endpoint.

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

Move into the project directory:

```bash
cd YOUR_REPOSITORY
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

## Model Setup

The application expects the fine-tuned model and tokenizer inside:

```text
saved_summary_model/
```

Make sure this folder is present before running the application.

If the model is hosted separately, download it and place it in the expected location.

## Running the Application

Start the FastAPI server using:

```bash
uvicorn app:app --reload
```

The application will normally be available at:

```text
http://127.0.0.1:8000
```

Open this address in your browser.

## GPU Support

The application automatically checks whether CUDA is available.

If a compatible GPU is available:

```text
CUDA → GPU
```

Otherwise:

```text
CPU → CPU
```

This allows the same application to run on both GPU and CPU environments.

## API Documentation

FastAPI automatically provides interactive API documentation.

After starting the application, open:

```text
http://127.0.0.1:8000/docs
```

You can use this page to test the `/summarize/` endpoint.

## Example Input

```text
Speaker 1: Good morning. Did you complete the project?

Speaker 2: Yes, I completed the implementation yesterday.

Speaker 1: Great. Have you tested it?

Speaker 2: Yes, I tested the application and the summarization is working correctly.
```

The model generates a shorter summary of the conversation.

## Future Improvements

- Add file upload support
- Support PDF and DOCX summarization
- Add multiple summarization models
- Add summary length controls
- Add user authentication
- Deploy the application online
- Add Docker support
- Host the model using Hugging Face Hub
- Improve summarization quality through further fine-tuning

## Author

**Sumit Raghav**
