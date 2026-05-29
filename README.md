# 🏥 VaaniCare — Multilingual Voice AI Health Assistant

> *"Accessible healthcare guidance for every Indian, in their own language, through their own voice."*

[![Python](https://img.shields.io/badge/Python-3.11-blue)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115-green)](https://fastapi.tiangolo.com)
[![React](https://img.shields.io/badge/React-18-61dafb)](https://reactjs.org)
[![Groq](https://img.shields.io/badge/Groq-LLaMA%203.3%2070B-orange)](https://groq.com)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 🌍 Problem

Rural India faces a severe healthcare accessibility crisis:

- **600M+** rural Indians have limited access to doctors
- **22** scheduled languages — most health apps support only English
- **70%** of rural population has low digital literacy
- **Delayed consultation** leads to preventable deaths
- Most healthcare AI apps require typing, reading, and English

---

## 💡 Solution

VaaniCare is a **voice-first, multilingual AI healthcare assistant** that allows rural users to describe symptoms in their native language and receive safe, grounded health guidance — completely through voice.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎙️ Voice Input | Speak in Telugu, Hindi, Tamil, Kannada, English |
| 🌐 Auto Language Detection | Unicode script analysis — no manual selection needed |
| 🔍 Symptom Extraction | LLaMA 3.3 70B understands rural Indian terms |
| 🏥 AI Triage | XLM-RoBERTa classifies Low/Moderate/High/Emergency |
| 🛡️ Safety Guardrails | 3-layer safety in 5 languages |
| 📚 RAG Guidance | FAISS retrieval prevents hallucinations |
| 💊 Health Guidance | Why it occurs, home remedies, OTC tips, what not to do |
| 🔊 Voice Response | gTTS speaks back in patient's language |
| 🗺️ Hospital Finder | OpenStreetMap — nearest PHC/hospital with directions |
| 📸 Photo Analysis | Groq Vision analyzes skin/wound photos |
| 💬 Multi-turn Chat | Full conversation memory across voice turns |

---

## 🏗️ Architecture
