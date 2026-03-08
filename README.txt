================================================================
  SQL QUERY GENERATOR
  Natural Language to SQLite SQL — IBM Granite 3.3 2B Instruct
================================================================

IBM Agentic AI Application Developer Program
SmartBridge / Skill Wallet
Deadline: 8th March

----------------------------------------------------------------
OVERVIEW
----------------------------------------------------------------
SQL Query Generator is an AI-powered application that converts
plain English requests into safe, production-ready SQLite SELECT
queries — no SQL knowledge required.

Example:
  Input : "Show me all active users who signed up last month"
  Output: SELECT * FROM users WHERE status = 'active'
          AND DATE(signup_date) >= DATE('now', '-1 month') LIMIT 10

----------------------------------------------------------------
FEATURES
----------------------------------------------------------------
  - AI-powered NL parsing (IBM Granite 3.3 2B Instruct)
  - SQL injection prevention (blocks DROP, DELETE, ALTER, etc.)
  - Smart table detection (users / orders / products / transactions)
  - Temporal filtering (last month, last week, this year, today)
  - PDF export (ReportLab)
  - TXT export (plain text history)
  - WhatsApp & Facebook social sharing links
  - Gradio chat interface with copy buttons and history

----------------------------------------------------------------
SUPPORTED DATABASE SCHEMA
----------------------------------------------------------------
  users        : id, name, email, signup_date, age, country, status
  orders       : id, user_id, product_name, amount, order_date, status
  products     : id, name, price, category, stock
  transactions : id, user_id, amount, date, type

----------------------------------------------------------------
GETTING STARTED (Google Colab)
----------------------------------------------------------------
Step 1 — Open Google Colab and enable GPU runtime
         Runtime > Change runtime type > GPU

Step 2 — Install dependencies
         !pip install -U transformers
         !pip install -q gradio transformers torch black autopep8 reportlab requests

Step 3 — Load IBM Granite Model
         from transformers import pipeline
         pipe = pipeline("text-generation",
                         model="ibm-granite/granite-3.3-2b-instruct")

Step 4 — Run the app
         python sql_query_generator.py
         (or paste code into a Colab cell and run)

Step 5 — Access the app via the public Gradio link printed in output
         e.g., https://xxxxxxxxx.gradio.live

----------------------------------------------------------------
PROJECT FILES
----------------------------------------------------------------
  granite_3_3_2b_instruct.ipynb   — Original Colab notebook
  sql_query_generator.py          — Main application code
  requirements.txt                — Python dependencies
  SQL_QG_Project_Summary.docx     — Full project documentation
  README.md / README.txt          — This file

----------------------------------------------------------------
REQUIREMENTS
----------------------------------------------------------------
  gradio
  transformers
  torch
  black
  autopep8
  reportlab
  requests

  Install: pip install -r requirements.txt

----------------------------------------------------------------
SECURITY
----------------------------------------------------------------
  Blocked Keywords : DROP, DELETE, ALTER, TRUNCATE, INSERT,
                     UPDATE, EXEC, EXECUTE
  Blocked Patterns : ;  --  /*  */  xp_  sp_
  Only SELECT statements are generated — no data modification.
  Automatic LIMIT 10 prevents full-table scans.

----------------------------------------------------------------
EXAMPLE QUERIES
----------------------------------------------------------------
  "Show all users who signed up last month"
  → SELECT * FROM users WHERE DATE(signup_date) >= DATE('now', '-1 month') LIMIT 10

  "Get active customers"
  → SELECT * FROM users WHERE status = 'active' LIMIT 10

  "Find transactions greater than 500 last week"
  → SELECT * FROM transactions WHERE amount > 500
    AND DATE(date) >= DATE('now', '-7 days') LIMIT 10

  "DROP TABLE users"  →  BLOCKED (SQL injection detected)

----------------------------------------------------------------
PROJECT MILESTONES
----------------------------------------------------------------
  M1 — Environment Setup   : Install packages, load Granite model
  M2 — Security & Schema   : is_safe(), SCHEMA dictionary
  M3 — NLP Engine          : Table detection, column mapping,
                             condition extraction
  M4 — Gradio UI & Export  : Chat interface, PDF/TXT, social sharing
  M5 — Testing & Deploy    : Tests + demo.launch(share=True)

----------------------------------------------------------------
TECH STACK
----------------------------------------------------------------
  Language   : Python 3.8+
  AI Model   : IBM Granite 3.3 2B Instruct (HuggingFace)
  UI         : Gradio
  NLP        : HuggingFace Transformers + Python Regex
  Database   : SQLite
  PDF        : ReportLab
  Platform   : Google Colab

----------------------------------------------------------------
SUBMISSION CHECKLIST
----------------------------------------------------------------
  [x] Source code (.py / .ipynb)
  [x] Project document (.docx)
  [x] README (this file)
  [ ] Demo video — upload to Google Drive
  [ ] GitHub repository — upload all files

----------------------------------------------------------------
FUTURE ENHANCEMENTS
----------------------------------------------------------------
  - JOIN operations across multiple tables
  - GROUP BY and aggregation (COUNT, SUM, AVG)
  - Custom database schema uploading
  - Query optimization suggestions
  - PostgreSQL / MySQL integration
  - Hugging Face Spaces deployment

----------------------------------------------------------------
  Built with IBM Granite 3.3 2B | SmartBridge | Skill Wallet
================================================================
