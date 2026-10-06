# 🩺 AI Medical Report Summarizer

## 📌 Project Description

**AI Medical Report Summarizer** is a Streamlit-based application that uses Artificial Intelligence to summarize medical reports.

The application allows users to upload a medical document in **PDF, TXT, or DOCX** format. It extracts the text from the uploaded document, cleans the text, sends it to an AI summarization model, and displays a clear medical report summary.

The generated summary can also be downloaded as a `.txt` file.

> ⚠️ **Disclaimer:** This application is intended only for summarization and educational purposes. It is not a substitute for professional medical advice, diagnosis, or treatment.

---

## ✨ Features

- 📄 Upload medical reports
- 📑 Supports PDF, TXT, and DOCX files
- 🔍 Extract text from uploaded documents
- 🧹 Clean extracted text before processing
- 🤖 Generate AI-powered summaries
- 📋 Display the generated medical summary
- 📥 Download the summary as a text file
- 📊 Handles both short and long medical reports
- 🌐 Simple and user-friendly Streamlit interface

---

## 🛠️ Technologies Used

- **Python**
- **Streamlit**
- **Google Gemini API**
- **PyPDF**
- **python-docx**
- **python-dotenv**

---

## 📁 Project Structure

```text
medical_report_summarizer/
│
├── app.py
├── requirements.txt
├── .env
│
└── utils/
    ├── __init__.py
    ├── extract_text.py
    ├── text_cleaner.py
    └── summarizer.py
```

### File Description

| File | Purpose |
|---|---|
| `app.py` | Main Streamlit application |
| `requirements.txt` | Contains required Python packages |
| `.env` | Stores the Gemini API key |
| `utils/extract_text.py` | Extracts text from PDF, TXT, and DOCX |
| `utils/text_cleaner.py` | Cleans and prepares extracted text |
| `utils/summarizer.py` | Sends text to the AI model and generates the summary |
| `utils/__init__.py` | Makes `utils` a Python package |

---

## 💻 Requirements

Before running the project, install:

- Python 3.10 or later
- Internet connection
- Google Gemini API key

---

## ⚙️ Installation

### Step 1: Clone or Download the Project

Download the project to your computer.

Open **Command Prompt** or **PowerShell** and move into the project folder:

```bash
cd "C:\AI Medical Report"
```

---

### Step 2: Create a Virtual Environment

```bash
python -m venv venv
```

Activate the virtual environment:

```bash
venv\Scripts\activate
```

After activation, you should see:

```text
(venv)
```

at the beginning of your terminal.

---

### Step 3: Install Required Packages

Run:

```bash
pip install -r requirements.txt
```

---

## 🔑 API Key Configuration

The application uses the **Google Gemini API** for generating summaries.

Create a file named:

```text
.env
```

in the main project folder.

Add your API key:

```env
GEMINI_API_KEY=your_api_key_here
```

Replace `your_api_key_here` with your actual Gemini API key.

### Important

Do not share your API key publicly or upload the `.env` file to GitHub.

You can add `.env` to `.gitignore`:

```text
.env
venv/
__pycache__/
```

---

## ▶️ How to Run the Application

Make sure your virtual environment is activated.

Run:

```bash
streamlit run app.py
```

Streamlit will start the application and provide a local address such as:

```text
http://localhost:8501
```

Open this address in your web browser.

---

## 🔄 Application Workflow

The application works in the following steps:

```text
        Start
          ↓
   Upload Medical Report
          ↓
     Extract Text
          ↓
      Clean Text
          ↓
    Check Text Length
       ↙       ↘
    Short       Long
      ↓           ↓
  Summarize   Long Text
      ↓       Summarization
       ↘       ↙
      Generate Summary
             ↓
      Display Summary
             ↓
      Download Summary
             ↓
            End
```

---

## 🧠 How the Code Works

### 1. Upload Document

The application uses Streamlit's file uploader:

```python
uploaded_file = st.file_uploader(
    "Upload your document",
    type=["pdf", "txt", "docx"]
)
```

This allows the user to upload PDF, TXT, or DOCX files.

---

### 2. Extract Text

The uploaded document is passed to:

```python
text = extract_text(uploaded_file)
```

The `extract_text()` function extracts readable text from the document.

---

### 3. Clean Text

The extracted text is cleaned using:

```python
cleaned_text = clean_text(text)
```

This prepares the text before sending it to the AI model.

---

### 4. Generate Summary

For shorter documents:

```python
summary = summarize_text(cleaned_text)
```

For longer documents:

```python
summary = summarize_long_text(cleaned_text)
```

The application uses different functions depending on the amount of extracted text.

---

### 5. Display Summary

The generated summary is displayed using:

```python
st.markdown(summary)
```

The user can read the AI-generated medical report summary directly in the application.

---

### 6. Download Summary

The summary can be downloaded using:

```python
st.download_button(
    label="📥 Download Summary",
    data=summary,
    file_name="medical_report_summary.txt",
    mime="text/plain"
)
```

This saves the summary as:

```text
medical_report_summary.txt
```

---

## 📄 Supported File Formats

| Format | Supported |
|---|---|
| PDF | ✅ |
| TXT | ✅ |
| DOCX | ✅ |
| JPG/PNG | ❌ |

---

## 🎯 Use Cases

This project can be useful for:

- Students learning AI application development
- Demonstrating document processing
- Summarizing lengthy medical reports
- Educational projects
- Understanding AI API integration
- Learning Streamlit application development

---

## ⚠️ Limitations

- The quality of the summary depends on the extracted text and AI model.
- Scanned/image-only PDFs may require OCR support.
- An internet connection is required for the AI API.
- API usage may have limits or costs depending on the API provider.
- AI-generated summaries may contain errors.
- The application should not be used for medical diagnosis or treatment decisions.

---

## 🚀 Future Enhancements

Possible future improvements include:

- 🖼️ OCR support for scanned medical reports
- 📊 Medical information visualization
- 🔎 Important finding detection
- 💊 Medicine and prescription extraction
- 📅 Date and patient information extraction
- 📝 Different summary formats
- 🌐 Multiple language support
- 📄 Export summary as PDF
- 🔐 Improved privacy and data protection
- 💬 Interactive question-answering about the uploaded report

---

## 🔒 Privacy and Security

Medical reports can contain sensitive information.

For a real-world deployment:

- Do not expose API keys in source code.
- Use environment variables for secrets.
- Avoid storing medical reports unnecessarily.
- Consider removing personally identifiable information.
- Use appropriate security and privacy controls before handling real patient data.

---

## 🧪 Testing

The application should be tested with:

1. A small TXT medical report.
2. A normal PDF medical report.
3. A DOCX medical report.
4. An empty document.
5. A very long medical report.
6. An unsupported file type.
7. A document from which no text can be extracted.

The application should display an appropriate error message when text cannot be extracted or an unexpected error occurs.

---

## 📌 Example

### Input

```text
Patient Name: Example Patient

The patient was evaluated during a routine examination.
Blood pressure was recorded and laboratory investigations
were performed. The report contains the patient's test
observations and clinical information.
```

### Output

```text
Medical Report Summary

The report contains information from a routine patient
evaluation, including blood pressure and laboratory
investigations.
```

---

## 📚 Learning Outcomes

By completing this project, you can learn:

- Python programming
- Streamlit application development
- File handling
- PDF and DOCX text extraction
- Text preprocessing
- AI API integration
- Prompt-based summarization
- Environment variables
- Error handling
- Creating downloadable files

---

## 👩‍💻 Project

**Project Name:** AI Medical Report Summarizer

**Technology:** Python + Streamlit + Google Gemini

**Application Type:** AI-powered document summarization

---

## 📜 Disclaimer

This project is developed for **educational and demonstration purposes**. The generated summary should not be considered medical advice, diagnosis, or treatment guidance. Always consult a qualified healthcare professional for medical decisions.
