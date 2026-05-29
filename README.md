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
Voice Input (Telugu/Hindi/Tamil/Kannada/English)
↓
Groq Whisper API — Speech to Text (< 2 seconds)
↓
Unicode Script Language Detection
↓
LLaMA 3.3 70B — Symptom Extraction via LangChain
↓
XLM-RoBERTa — Triage Classification
(Low → Moderate → High → Emergency)
↓
Safety Guardrails — 3-layer validation
↓
FAISS Vector Search — RAG Medical Knowledge
↓
LLaMA 3.3 70B — Response Generation
(Why it occurs + Home remedies + OTC tips + Warnings)
↓
Final Safety Validation
↓
gTTS — Text to Speech in patient's language
↓
OpenStreetMap — Nearby Hospital Recommendations
↓
Voice Response + Guidance + Map to User
---

## 🛠️ Technology Stack

### Backend
| Component | Technology |
|---|---|
| API Framework | FastAPI |
| Speech-to-Text | Groq Whisper Large v3 Turbo |
| LLM | Groq LLaMA 3.3 70B |
| LLM Framework | LangChain LCEL |
| Triage Model | Fine-tuned XLM-RoBERTa |
| Vector DB | FAISS |
| Embeddings | sentence-transformers (multilingual) |
| Text-to-Speech | gTTS |
| Vision AI | Groq Llama 4 Scout |
| Facility Search | OpenStreetMap Overpass API |
| Audio Processing | ffmpeg |

### Frontend
| Component | Technology |
|---|---|
| Framework | React 18 |
| Maps | Leaflet + react-leaflet |
| HTTP Client | Axios |
| Icons | Lucide React |
| Fonts | Sora + Noto Sans Telugu |

### Deployment
| Component | Technology |
|---|---|
| Backend | Render |
| Frontend | Render Static |
| Version Control | GitHub |

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11+
- Node.js 18+
- ffmpeg installed
- Groq API key (free at console.groq.com)

### Backend Setup

```bash
# Clone the repo
git clone https://github.com/pallavidondapati/health_care.git
cd health_care

# Create virtual environment
python -m venv venv
venv\Scripts\activate  # Windows
source venv/bin/activate  # Linux/Mac

# Install dependencies
pip install -r requirements.txt

# Create .env file
echo GROQ_API_KEY=your_key_here > .env

# Train triage model (optional)
python -m backend.ml.prepare_data
python -m backend.ml.train

# Start backend
uvicorn backend.main:app --reload
```

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

### Environment Variables

```bash
# .env
GROQ_API_KEY=your_groq_api_key_here
```

---

## 📡 API Endpoints

| Endpoint | Method | Description |
|---|---|---|
| `GET /health` | GET | Health check |
| `POST /api/vaanicare` | POST | Full pipeline — audio in, guidance out |
| `POST /api/transcribe` | POST | Speech to text (Groq Whisper) |
| `POST /api/extract-symptoms` | POST | Symptom extraction (LLaMA) |
| `POST /api/triage` | POST | Severity classification (XLM-R) |
| `POST /api/safety-check` | POST | Safety validation |
| `POST /api/generate-response` | POST | RAG + LLM response |
| `POST /api/text-to-speech` | POST | Text to audio (gTTS) |
| `POST /api/nearest-facility` | POST | Nearby hospitals (OSM) |
| `POST /api/analyze-photo` | POST | Vision AI photo analysis |

---

## 🗂️ Project Structure
health_care/
├── backend/
│   ├── init.py
│   ├── main.py                 # FastAPI app
│   ├── api/
│   │   ├── init.py
│   │   ├── speech.py           # Groq Whisper STT
│   │   ├── symptom.py          # LangChain symptom extraction
│   │   ├── triage.py           # XLM-R triage classifier
│   │   ├── safety.py           # Safety guardrails
│   │   ├── response.py         # RAG + LLM response
│   │   ├── tts.py              # Text to speech
│   │   ├── facility.py         # Hospital finder
│   │   ├── photo.py            # Vision AI
│   │   └── vaanicare.py        # Full pipeline
│   └── ml/
│       ├── knowledge_base.py   # Medical knowledge docs
│       ├── rag.py              # FAISS vector search
│       ├── prepare_data.py     # Training data
│       └── train.py            # XLM-R fine-tuning
├── frontend/
│   ├── public/
│   └── src/
│       ├── App.js
│       └── pages/
│           ├── Home.jsx        # Voice interface + chat
│           ├── Result.jsx      # Results display
│           ├── HospitalMap.jsx # Leaflet map
│           └── PhotoAnalysis.jsx # Photo upload
├── requirements.txt
├── render.yaml
├── runtime.txt
└── .gitignore
---

## 🛡️ Safety Design

VaaniCare is built with healthcare safety as the top priority:

1. **Emergency Override** — 30+ emergency keywords in 5 languages instantly escalate to "Call 108"
2. **Non-Emergency Downgrade** — Common symptoms like sore throat, cold, cough cannot be falsely classified as emergency
3. **Medicine Filter** — AI responses scanned for prescription medicine names, antibiotic suggestions, dosage recommendations
4. **RAG Grounding** — All responses grounded in verified medical knowledge to prevent hallucinations
5. **No Diagnosis** — System never diagnoses diseases, only provides guidance
6. **Doctor Referral** — Every response includes clear guidance on when to visit a doctor

---

## 🌐 Supported Languages

| Language | Code | Script Detection |
|---|---|---|
| Telugu | te | ✅ |
| Hindi | hi | ✅ |
| Tamil | ta | ✅ |
| Kannada | kn | ✅ |
| Malayalam | ml | ✅ |
| English | en | ✅ |

---

## 🤖 AI/ML Concepts

- ✅ Transformer fine-tuning (XLM-RoBERTa)
- ✅ Cross-lingual transfer learning
- ✅ Multilingual NLP
- ✅ Speech AI (Whisper)
- ✅ Retrieval Augmented Generation (RAG)
- ✅ Vector similarity search (FAISS)
- ✅ AI safety engineering
- ✅ Multimodal AI (vision + speech + text)
- ✅ LangChain LCEL pipelines
- ✅ Healthcare AI systems

---

## 🌱 Social Impact

VaaniCare directly addresses UN Sustainable Development Goal 3 — Good Health and Well-Being:

- **Remote villages** — Voice health access without smartphone literacy
- **Non-literate users** — Complete voice interface, no reading required
- **Elderly patients** — Simple interaction in native language
- **Tribal regions** — Low-resource Indian language support
- **Low-income families** — Free, 24/7 accessible health guidance
- **Women in rural areas** — Safe, private health consultation

---

## 📈 Future Roadmap

- [ ] Offline inference support for zero-connectivity areas
- [ ] Telemedicine integration — connect to real doctors
- [ ] Wearable sensor data integration
- [ ] Medical image upload (X-ray, reports)
- [ ] Health history memory across sessions
- [ ] ASHA worker dashboard
- [ ] Multilingual health analytics
- [ ] WhatsApp integration for wider reach

---

## 👩‍💻 Author

**Pallavi Dondapati**
- GitHub: [@pallavidondapati](https://github.com/pallavidondapati)
- Project: [health_care](https://github.com/pallavidondapati/health_care)

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## ⚠️ Disclaimer

VaaniCare is an AI-powered health guidance tool and does not replace professional medical advice. Always consult a qualified doctor for diagnosis and treatment. In emergencies, call 108 immediately.

---

*Built with ❤️ for rural India*
