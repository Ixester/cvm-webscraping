## Description

This repository involves extracting quarterly reports from publicly traded companies through web scraping from the Brazilian Securities and Exchange Commission (CVM) website. These reports were processed, converted to `.txt` format, and stored in an AWS S3 bucket.

### Repository Steps

1. **Web Scraping from CVM:**
   - We accessed the CVM database through the document search site for publicly traded companies [CVM Documents](https://www.rad.cvm.gov.br/ENET/frmConsultaExternaCVM.aspx).
   - We extracted all quarterly reports from companies listed at least once on the current B3 or the former IBOVESPA.
   - The documents date back to 2010 and are in PDF format.

2. **Extracted Data:**
   - We extracted 11,222 quarterly reports from 368 companies, totaling 19.53GB in size.
   - These reports are available for download [here](https://drive.google.com/drive/folders/1M5u6r2nS-JcLhaZSJTYJVeiCTOogoEGG?usp=drive_link).

3. **PDF to TXT Conversion:**
   - All PDF files were converted to `.txt` format using the `Fitz` and `OS` libraries in Python.
   - The conversion code is available in the `Noie.py` file.

4. **S3 Storage:**
   - After conversion, the `.txt` files were stored in an AWS S3 bucket.

5. **Web Scraping and Processing with Python:**
   - The `Noie.py` script performs data extraction from the CVM site.
   - The `OIE - S3AWS.py` script is responsible for uploading the converted files to S3 and analyzing keywords in the extracted texts.
   - To perform web scraping and upload, follow the steps below.

## Requirements

- Python 3.x
- Libraries:
  - Fitz (PyMuPDF)
  - OS
  - Boto3 (for S3 upload)
  - SpaCy (for natural language processing)
  - Matcher (from SpaCy for pattern recognition)

## Usage

### Web Scraping and PDF to TXT Conversion

1. Set up your Python environment with the required libraries:
   ```bash
   pip install pymupdf boto3 spacy
   ```
2. Run the web scraping and PDF to TXT conversion script:
   ```bash
   python Noie.py
   ```

### Upload and Processing in AWS S3

1. Ensure your AWS credentials are configured in your environment.
2. Run the upload and processing script:
   ```bash
   python OIE - S3AWS.py
   ```

## Download Links

- [Quarterly Reports - Google Drive](https://drive.google.com/drive/folders/1M5u6r2nS-JcLhaZSJTYJVeiCTOogoEGG?usp=drive_link)
