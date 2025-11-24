# AI-Powered Resume Analyzer with OpenAI and Azure

[![Python Version](https://img.shields.io/badge/python-3.10-blue.svg)](https://www.python.org/downloads/release/python-3104/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.0+-red.svg)](https://streamlit.io/)
[![LangChain](https://img.shields.io/badge/LangChain-Latest-green.svg)](https://python.langchain.com/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 📋 Overview

An intelligent resume analysis system that leverages Large Language Models (LLMs) to help job seekers optimize their resumes against specific job descriptions. This AI-powered tool goes beyond simple keyword matching to understand the semantic context of both resumes and job descriptions, providing personalized insights and actionable recommendations.

### Key Features

- **Semantic Resume Matching**: Uses OpenAI embeddings to calculate similarity scores between resumes and job descriptions
- **Gap Analysis**: Identifies missing skills, qualifications, and experience
- **Personalized Suggestions**: Provides actionable recommendations for resume improvement
- **Multi-Format Support**: Processes both PDF and image-based resumes using OCR
- **Interactive Chat Interface**: User-friendly Streamlit application for real-time feedback
- **Cloud Deployment**: Scalable deployment on Microsoft Azure

## 🎯 Project Goals

This project addresses the needs of job seekers who want to:
- Proactively assess their resumes against job descriptions
- Identify skill gaps and areas for improvement
- Receive AI-driven, personalized insights
- Understand how well their experience aligns with job requirements
- Optimize resume formatting and content

## 🏗️ Architecture

```
┌─────────────┐
│   Resume    │
│     PDF     │
└──────┬──────┘
       │
       ├─────────────┐
       │             │
┌──────▼──────┐ ┌───▼────────┐
│ PDF Reader  │ │ Image OCR  │
└──────┬──────┘ └───┬────────┘
       │            │
       └────┬───────┘
            │
    ┌───────▼────────┐
    │   LangChain    │
    │   GPT-4        │
    │   Embeddings   │
    └───────┬────────┘
            │
    ┌───────▼────────┐
    │   Streamlit    │
    │   Interface    │
    └────────────────┘
```

## 🚀 Getting Started

### Prerequisites

- Python 3.10.4
- pip package manager
- OpenAI API Key
- Poppler (for PDF processing)
- Tesseract (for OCR)

### System Dependencies

#### Installing Poppler

**Windows:**
1. Download from [poppler-windows releases](https://github.com/oschwartz10612/poppler-windows/releases/)
2. Extract to `C:\poppler`
3. Add `C:\poppler\bin` to system PATH

**Mac:**
```bash
brew install poppler
```

#### Installing Tesseract

**Windows:**
1. Download from [Tesseract Wiki](https://github.com/UB-Mannheim/tesseract/wiki)
2. Run installer and add to PATH

**Mac:**
```bash
brew install tesseract
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/resume-analyzer.git
cd resume-analyzer
```

2. **Create virtual environment**

**Windows:**
```bash
python -m venv venv
.\venv\Scripts\activate
```

**Mac/Linux:**
```bash
python3.10 -m venv venv
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure API Keys**

Create a `constants.py` file in the `src` directory:
```python
OPENAI_API_KEY = "your-openai-api-key-here"
```

### Running the Application

```bash
streamlit run src/resume_suggestions.py
```

The application will launch in your default web browser at `http://localhost:8501`

## 📁 Project Structure

```
resume-analyzer/
├── jd_data/                  # Job description files
├── resume_data/              # Resume files
├── output/                   # Generated embeddings
│   ├── jd_embeddings_large.pkl
│   └── resume_embeddings_large.pkl
├── src/
│   ├── constants.py          # API keys and configuration
│   ├── directory_reader.py   # File reading utilities
│   ├── embedding_model.py    # Embedding generation
│   ├── resume_scorer.py      # Similarity scoring
│   └── resume_suggestions.py # Streamlit application
├── Resume_Scorer.ipynb       # Jupyter notebook for scoring
├── Resume_Suggestions.ipynb  # Jupyter notebook for suggestions
├── requirements.txt          # Python dependencies
└── readme.md                # This file
```

## 💡 How It Works

### 1. Document Processing
- Extracts text from PDF resumes and job descriptions
- Uses OCR (Tesseract) for image-based documents
- Standardizes and preprocesses text data

### 2. Embedding Generation
- Creates semantic embeddings using OpenAI's `text-embedding-3-large` model
- Captures contextual meaning beyond simple keywords
- Stores embeddings for efficient similarity comparison

### 3. Similarity Analysis
- Calculates cosine similarity between resume and job description embeddings
- Generates matching scores (0-100 scale)
- Ranks resumes based on alignment with job requirements

### 4. Gap Analysis
- Identifies missing skills and qualifications
- Highlights areas where the resume doesn't align with job requirements
- Provides context-aware recommendations

### 5. AI-Powered Suggestions
- Uses GPT-4 to generate personalized improvement recommendations
- Suggests relevant skills to acquire
- Recommends action words and formatting improvements
- Provides tailored advice based on specific job requirements

## 🔧 Technical Stack

- **Language**: Python 3.10
- **LLM Framework**: LangChain
- **Models**: 
  - GPT-4 for text generation and analysis
  - text-embedding-3-large for semantic embeddings
- **UI Framework**: Streamlit
- **PDF Processing**: PyPDF2, pdf2image
- **OCR**: Pytesseract
- **Vector Storage**: FAISS (Facebook AI Similarity Search)
- **Cloud Platform**: Microsoft Azure (for deployment)

## 📊 Key Components

### LangChain Integration
- **Model I/O**: Manages interactions with OpenAI models
- **Prompts**: Structured prompt engineering for consistent results
- **Output Parsers**: Formats LLM responses into structured data
- **Chains**: Sequences operations for complex workflows
- **Memory**: Maintains conversation context

### Streamlit Features
- File upload for resumes and job descriptions
- Interactive chat interface
- Real-time analysis and feedback
- Visual similarity scores
- Downloadable recommendations

## 💰 Cost Estimation

### OpenAI API Costs (as of January 2025)
- **GPT-4o**: Input $0.06/1K tokens, Output $0.18/1K tokens
- **Embeddings**: $0.00013/1K tokens
- **Example**: Processing 100 resumes ≈ $2.16/month

### Azure Deployment
- **Free Tier**: Available for development and testing
- **Basic (B1)**: ~$13/month for production workloads
- **Storage**: ~$0.02/GB/month

**Estimated Total**: $2-15/month for small-scale usage

## 🎓 Learning Outcomes

- Understanding LLM applications in real-world scenarios
- Semantic search and embeddings
- Prompt engineering best practices
- LangChain framework fundamentals
- Building interactive ML applications with Streamlit
- Cloud deployment on Azure
- Working with unstructured text data
- Vector similarity and cosine distance

## 📈 Use Cases

### For Job Seekers
- Optimize resumes for specific job postings
- Identify skill gaps before applying
- Receive objective, AI-driven feedback
- Track resume improvements over time
- Tailor applications for different roles

### For Employers
- Quickly screen large volumes of resumes
- Reduce unconscious bias in initial screening
- Identify top candidates efficiently
- Provide constructive feedback to applicants

## 🔒 Privacy & Security

- All processing is done in-memory
- No resume data is permanently stored
- OpenAI API calls are encrypted
- User data is never shared with third parties
- Complies with data protection regulations

## 🚧 Roadmap

- [ ] Support for additional file formats (DOCX, TXT)
- [ ] Multi-language support
- [ ] Resume template generator
- [ ] Batch processing for multiple resumes
- [ ] Advanced analytics dashboard
- [ ] Integration with job boards (LinkedIn, Indeed)
- [ ] Mobile application

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for GPT-4 and embedding models
- LangChain for the excellent framework
- Streamlit for the intuitive UI framework
- The open-source community

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

**Note**: This project is for educational purposes. Always review AI-generated suggestions before applying them to your resume.
