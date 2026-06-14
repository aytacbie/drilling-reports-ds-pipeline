# Drilling Reports — Data Science Pipeline

A three-stage data science pipeline for extracting, matching, and analyzing oil drilling reports.

## Overview

This project processes 1,000 PDF drilling reports, extracts structured data into a SQLite database, performs NDS (Non-Drilling Surprise) event matching, and applies NLP analysis with anomaly detection.

## Tasks

### Task 1 — PDF Parsing
Extracts structured tables (drilling fluid, operations, wellbore metadata) from 1,000 PDF reports using `pdfplumber`. Handles multi-page table splits and stores results in a SQLite database.

### Task 2 — NDS Event Matching
Matches NDS events from an Excel file to drilling operations in the database using TF-IDF similarity and rule-based matching (scikit-learn). Outputs a ranked match results file.

### Task 3 — NLP Analysis
- Named Entity Recognition (NER) on drilling report text
- Anomaly detection using Isolation Forest on operational parameters
- Time-series trend analysis across wellbores

## Project Structure

```
Task_DS/
├── task1_pdf_parsing.ipynb      # PDF extraction → SQLite
├── task2_nds_matching.ipynb     # NDS event matching (TF-IDF)
├── task3_nlp_analysis.ipynb     # NLP + anomaly detection
├── drilling_reports.db          # Output SQLite database
├── nds_events.xlsx              # Input NDS events
├── nds_matching_results.xlsx    # Task 2 output
├── nlp_analysis_results.xlsx    # Task 3 output
└── PDF_version_1000/            # 1,000 input PDFs (not tracked)
```

## Tech Stack

- **PDF parsing:** pdfplumber
- **Database:** SQLite (sqlite3)
- **NLP / ML:** scikit-learn (TF-IDF, Isolation Forest)
- **Data:** pandas, numpy
- **Visualization:** matplotlib

## How to Run

1. Place the `PDF_version_1000/` folder in the project directory
2. Run notebooks in order: `task1` → `task2` → `task3`
3. Each notebook reads from / writes to `drilling_reports.db`
