# ArXiv_Summariser

Research Paper Summarization System
A multi-agent system that finds, analyzes, and summarizes research papers from various sources, organizes them by topic, and generates audio summaries.

Features
Three Input Methods: Keyword search (using ArXiv API), PDF file upload, URL link to PDF

Automated Processing Pipeline: Paper discovery and fetching, Text extraction and cleaning, Chunking and summarization, Final summary generation

Future Audio Support: Text-to-speech conversion, Podcast-style output

Installation
Prerequisites
Python 3.8 or higher
pip package manager

Setup
Clone the repository:

bash
git clone https://github.com/yourusername/research-paper-summarizer.git
cd research-paper-summarizer
Create and activate a virtual environment (recommended):

bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate    # Windows
Install dependencies:

bash
pip install -r requirements.txt
Usage
Running the Application
Start the Streamlit interface:

bash
 py -m streamlit run app.py
 
Input Options
Keyword Search: Enter keywords related to your research interest, System will fetch relevant papers from ArXiv

PDF Upload: Upload a PDF research paper directly, System will process the uploaded file

URL Input: Paste a URL to a PDF research paper, System will download and process the paper

Output
The system will display:
Extracted paper metadata (title, authors, etc.)
Generated summary

(Future) Audio podcast download option
System Architecture
The system follows a modular pipeline architecture:
Input Interface (Streamlit)

Processing Modules:
Paper fetcher (ArXiv API)
PDF downloader
Text extractor
Content cleaner
Text chunker
Summarizer (chunk and final)

Output Interface (Streamlit)

Documentation
Key Modules
fetch_paper.py: Fetches papers from ArXiv using keywords
download_pdf.py: Downloads PDFs from URLs
extract_text.py: Extracts text from PDF files
cleanContent.py: Cleans and preprocesses extracted text
chunk_text.py: Splits text into manageable chunks
summarize_chunks.py: Generates summaries of text chunks
generate_final_summary.py: Creates final comprehensive summary

For detailed module documentation, see the inline comments in each file.

Limitations
Currently only supports ArXiv for keyword searches
Basic text extraction may struggle with complex PDF layouts
Audio generation is not yet implemented
Summarization quality depends on the current model

Future Improvements
Integrate additional paper sources (Semantic Scholar, Google Scholar)
Implement PyMuPDF + pdfplumber for better PDF processing
Upgrade to more advanced summarization models (Mistral 7B, Phi-3)
Add audio podcast generation

Implement topic modeling and organization
Sample Usage
Keyword Search Example
python
from fetch_paper import ArxivPaperFetcher

fetcher = ArxivPaperFetcher()
papers = fetcher.fetch_papers("large language models", max_results=5)

PDF Processing Example
python
from download_pdf import PdfDownloader
from extract_text import PdfTextExtractor
from cleanContent import ContentCleaner

# Download PDF
pdf_bytes = PdfDownloader.download_pdf("https://arxiv.org/pdf/1706.03762.pdf")

# Extract and clean text
text = PdfTextExtractor.extract_text(pdf_bytes)
clean_text = ContentCleaner.clean_text(text)

Requirements
See requirements.txt for complete list:
streamlit==1.32.0
requests==2.31.0
feedparser==6.0.10
PyPDF2==3.0.1
transformers==4.40.0
torch==2.2.0
regex==2023.10.3
