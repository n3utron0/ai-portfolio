Applied LLM & RAG Systems – Portfolio
This repository showcases three end-to-end applied AI systems built with Python, LLM APIs, and production-style architectures. The focus is on LLM integration, RAG, stateful workflows, and reliability, not on model training.

Project 1: LLM-Powered Resume Screening System (ATS)
Problem
Manual resume screening is slow, inconsistent, and hard to scale across large applicant pools.
Solution
An end-to-end ATS-style pipeline that ingests resume PDFs, cleans and normalizes text, applies LLM-based structured extraction against a given JD, and stores results for ranking, filtering, and review via a Streamlit UI.
Key Highlights
•	PDF resume ingestion, text extraction (PyMuPDF), and deterministic text cleaning
•	Heuristic metadata extraction for name/email/phone via regex to reduce LLM cost
•	Single LLM call that returns schema-constrained JSON (skills, experience, match score, reasoning)
•	MySQL persistence to enable ranking, filtering, analytics, CSV export, and optional email outreach
•	Streamlit UI for uploading resumes/JDs and reviewing shortlisted candidates
Tech Stack
Python • LLM APIs • PyMuPDF • Regex • MySQL • Streamlit
Repository: (link to ATS project)

Project 2: Agentic RAG-Based Loan & EMI Assistant
Problem
Loan and EMI queries need consistent, explainable answers based on documents and strict financial rules, not hallucinated math.
Solution
A stateful, agentic chatbot that combines RAG-backed document Q&A with deterministic EMI and loan-eligibility tools, orchestrated via explicit conversation state and a supervisor.
Key Highlights
•	ConversationState object for slots, context, and flow tracking across turns
•	Deterministic EMI and loan-eligibility tools; LLMs only used for intent detection, slot extraction, and answer validation
•	RAG pipeline: PDF extraction, chunking, embeddings, and vector search for grounded answers
•	Supervisor + intent router to handle interruptions, topic switches, and correct tool routing
•	FastAPI + LangGraph-based orchestration for inspectable, testable flows
Tech Stack
Python • FastAPI • LangGraph (agent orchestration) • LLM APIs • Embeddings • Vector store
Repository: (link to RAG loan assistant project)

Project 3: LLM-Based Telecom Call Analyzer
Problem
Manually reviewing large volumes of customer support calls to understand complaints, sentiment, and trends is costly and slow.
Solution
An async, cloud-native backend that processes call recordings, uses LLMs to extract structured complaint/sentiment data, stores it in BigQuery, and exposes both an operator UI and a natural-language analytics interface.
Key Highlights
•	Async pipeline: local audio → GCS upload → Gemini analysis → structured JSON → BigQuery
•	Strict JSON validation, retry/backoff, and metrics tracking for robust batch processing
•	Human-in-the-loop web UI for reviewing and confirming extracted fields before insertion
•	Natural-language → SQL layer that validates and executes safe SELECT-only queries on BigQuery
•	Centralized configuration and logging for predictable behavior and easier debugging
Tech Stack
Python • FastAPI • LLM APIs (Gemini) • Google Cloud Storage • BigQuery • HTML/JS frontend
Repository: (link to telecom analyzer project)

Design Philosophy
•	Use LLMs where they add semantic reasoning, not for math or basic parsing
•	Prefer deterministic tools and explicit state for critical logic and control flow
•	Keep architectures modular with clear separation of concerns (extraction, logic, storage, UI)
•	Build production-style pipelines, avoiding ad-hoc notebooks and purely prompt-only demos

Notes for Interviewers
•	Projects are implemented as working prototypes, focused on realistic workflows and constraints.
•	LLM usage is deliberately constrained (JSON schemas, validation, safety checks) rather than free-form chat.
•	Happy to walk through design choices, limitations, and possible next steps (evaluation, scaling, monitoring, etc.).
