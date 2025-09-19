# PropWise – UK Real Estate Price Forecaster & Advisor

PropWise is a **production-ready AI-powered property intelligence platform** designed to transform the way property buyers, investors, and advisors analyze the UK real estate market.  
The system combines **price forecasting**, **tax advisory**, and **continuous learning via RLHF** (Reinforcement Learning with Human Feedback) to deliver accurate, personalized property insights.
       
---

## 🚀 Final Project Highlights
- **✅ Full Production Deployment:** Backend & frontend deployed on **Google Cloud Run**.  
- **✅ Advanced RLHF System:** Multi-factor reward model for continuous learning and improvement.  
- **✅ End-to-End Integration:** Seamless integration between frontend, backend, and BigQuery.  
- **✅ Professional User Interface:** Gradio-based dashboard with advanced visual analytics.  
- **✅ Scalable Architecture:** Auto-scaling services with robust error handling and high uptime.

---

## 📊 Performance Metrics
| **Metric**           | **Value**         | **Status** |
|----------------------|-------------------|------------|
| **System Uptime**    | 99.2%            | ✅ Excellent |
| **User Satisfaction**| 85% positive ratings | ✅ High |
| **Query Success Rate** | 95%             | ✅ Reliable |
| **Response Latency** | 25-35 seconds    | ⚠️ Above target |
| **Feature Completion** | 100%           | ✅ Delivered |

**Why Latency is Acceptable:**  
- Complex multi-candidate generation with RLHF scoring.  
- Prioritizes **accuracy and comprehensive insights** over speed.  
- User experience mitigations include:
  - Progress indicators with clear loading messages.
  - Cached regional data for instant visualizations.

---

## 🏗️ System Architecture

### **Production Environment**
┌─────────────────────────────────────────────────────────────┐
│ Production Environment │
├─────────────────────────────────────────────────────────────┤
│ Frontend (Gradio): propwise-frontend │
│ └─ Port: 8600 │
│ └─ Auto-scaling: 0-10 instances │
├─────────────────────────────────────────────────────────────┤
│ Backend (FastAPI): propwise-backend │
│ └─ Port: 8080 │
│ └─ Auto-scaling: 0-10 instances │
└─────────────────────────────────────────────────────────────┘

### **Data Flow**
User Query → Frontend (Gradio) → Backend (FastAPI) → RLHF Manager
↓
BigQuery Context ← Embedding Service ← Multiple Candidates
↓
Reward Model Scoring → Best Response → Frontend Display
↓
User Feedback → Stored in BigQuery → Continuous Learning

---

## 🧠 Key Features

### **1. AI Forecasting**
- Short-term **property price predictions** by postcode sector.  
- Powered by **Vertex AI models** with integrated news sentiment analysis.

### **2. Tax Impact Module**
- **Stamp Duty Land Tax (SDLT)** calculator using up-to-date HMRC rules.
- **Rental Yield Estimation** for evaluating investment potential.
- **Capital Gains Tax (CGT)** forecasting for projected appreciation.

### **3. Conversational AI Advisor**
- Fine-tuned **PaLM-2 LLM** provides narrative, data-driven recommendations.  
- Example:
  > "In Leeds LS1, with a forecasted 3% rise and 3.5% gross yield, SDLT at £0–£250k is 0%, making it ideal for first-time buyers."

### **4. RLHF Continuous Learning**
- Multi-factor reward model:
  - **40%** User Ratings  
  - **30%** Context Relevance  
  - **20%** Forecast Accuracy  
  - **10%** Tax Accuracy  
- Weekly retraining cycles to improve response quality over time.

### **5. Interactive Dashboard**
- **AI Advisor Tab:** Conversational interface with ratings and session tracking.
- **Forecast Visualizations:** Postcode- and region-level insights with CSV export.
- **RLHF Analytics:** Tracks system performance and model improvement.
- **Professional Dark Mode UI:** Mobile responsive with a modern design.

---

## 📂 Repository Structure
propwise/
├── backend/ # FastAPI backend services
│ ├── tax/ # SDLT, CGT, rental yield calculators
│ ├── rl_training/ # RLHF reward models and training
│ └── main.py # API entrypoint
├── frontend/ # Gradio-based user interface
│ └── gradio_app.py
├── data_pipelines/ # BigQuery ingestion and ETL scripts
├── models/ # Forecasting and embedding models
└── docs/ # Documentation and reports

---

## ⚙️ Deployment Details

### Backend Dockerfile

```dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8080
CMD ["sh", "-c", "uvicorn main:app --host 0.0.0.0 --port ${PORT:-8080} --log-level debug"]
```
Key Dependencies:

fastapi, uvicorn[standard]

google-cloud-bigquery, google-cloud-aiplatform

vertexai

pandas, numpy
## Frontend Dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY gradio_app.py .
EXPOSE 8600
ENV GRADIO_SERVER_NAME="0.0.0.0"
ENV GRADIO_SERVER_PORT=8600
CMD ["python", "gradio_app.py"]
Key Dependencies:

gradio for interactive interface

plotly for visualizations

requests for backend communication

🔐 Security & Compliance

IAM Roles: Fine-grained access control for all GCP services.

HTTPS-only endpoints for secure data transfer.

GDPR-Compliant: No PII storage; anonymized user session tracking only.

Audit Logging: Full traceability of system operations.

📊 Analytics & Usage

Feedback Collected: 1,000+ user ratings during testing.

Top Usage Types:

Price Forecasting – 40%

Tax Calculations – 30%

Market Trends – 20%

Peak Usage Hours: 9-11 AM and 2-4 PM GMT.

Returning Users: 60% retention rate.

🗺️ Future Roadmap

Latency Optimization: Target 15-20s response times via:

Async RLHF candidate generation.

Query caching and database optimization.

Migration to latest Vertex AI SDK.

Advanced Features:

Property image-based analysis.

Personalized recommendation engine.

Real-time data streaming with BigQuery.

Platform Expansion:

Native iOS and Android apps.

White-label version for real estate agencies.

Support for international property markets.

📝 Lessons Learned

Deployment Best Practices: Proper health checks are essential for stable Cloud Run operations.

Performance vs Accuracy: Chose comprehensive, accurate responses over minimal latency.

Monitoring: Proactive monitoring and alerts are critical for production readiness.

User Feedback: Continuous feedback collection drives meaningful system improvements.
| **Status**             | **Result**                         |
| ---------------------- | ---------------------------------- |
| **Production System**  | ✅ Fully Operational                |
| **Project Completion** | ✅ 100% Objectives Achieved         |
| **Deployment**         | ✅ Production-Ready                 |
| **Performance**        | ⚠️ Stable at 25-35s latency        |
| **Handover**           | ✅ Complete Documentation Delivered |

