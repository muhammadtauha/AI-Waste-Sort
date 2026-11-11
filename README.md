♻️ AI-Powered Smart Waste Sorting (MERN + Python)

An intelligent web-based waste classification system that helps users identify and sort waste using AI. This project combines the MERN stack with a TensorFlow/Keras model to promote sustainable recycling habits through automation and gamification.

🚧 Project Status

⚠️ This project is currently under development
✔️ Core structure and partial features implemented
🔄 Remaining features are in progress (see TODO section below)

🎯 Purpose
Classify waste into categories (Plastic, Metal, Paper, Organic, etc.)
Encourage recycling through gamification (points, badges, leaderboard)
Provide insights and analytics for user contributions
Build a scalable AI-powered environmental solution
🏗️ Architecture Overview
Frontend (React + Vite)
        ↓
Backend API (Node.js + Express + MongoDB)
        ↓
AI Inference Service (Python + FastAPI + YOLO)
📁 Folder Structure
project-root/
│
├── ai-waste-sort/          # React app (UI)
├── backend/
│   ├── base_server/        # Node.js + Express REST API
│   ├── main.py             # FastAPI inference service (/scan)
│   ├── train.py            # Model training script
│   ├── data/               # Training dataset (dataset-resized/)
│   └── requirements.txt    # Python dependencies
├── docker-compose.yml
└── README.md
⚙️ Tech Stack
💻 Frontend
React.js
Tailwind CSS
Chart.js / Recharts
🧠 Backend
Node.js
Express.js
MongoDB (Mongoose)
🤖 AI / ML
Python
TensorFlow / Keras / Ultralytics (YOLO)
FastAPI (Inference API)
🚀 DevOps
Docker & Docker Compose
GitHub Actions (planned)
Vercel / Railway (deployment planned)
✅ Features Implemented
✔️ Basic project structure (MERN + Python)
✔️ Backend API setup (Express + MongoDB)
✔️ Image upload endpoint (partial)
✔️ Flask inference service (basic setup)
✔️ Initial React UI (Upload component)
✔️ Database schemas (User, Prediction)
🔄 Features In Progress (TODO)
🧠 AI & Backend
 Complete model training (train.py)
 Improve prediction accuracy
 Connect backend with inference service
 Add authentication (JWT)
🎨 Frontend
 Dashboard UI (analytics & charts)
 User profile with points & badges
 Upload preview & result display
🎮 Gamification
 Points system integration
 Achievement badges
 Leaderboard (global & weekly)
📊 Analytics
 Waste statistics (per category)
 User activity tracking
 CO₂ savings estimation
🌍 Community Features
 Recycling centers map
 User-submitted locations
 Weekly eco challenges
🛡️ Quality & Security
 Anti-spam limits
 Flagging system for wrong predictions
 Admin moderation panel
🚀 DevOps & Deployment
 Dockerfiles for all services
 Full docker-compose setup
 CI/CD pipeline (GitHub Actions)
 Deployment (Vercel + Railway + MongoDB Atlas)
🧪 API Example
Upload & Predict Waste
POST /api/upload

Request:

Image file

Response:

{
  "label": "Plastic",
  "confidence": 0.87
}
🗄️ Database Models
User
name
email
password
points
badges[]
Prediction
user
image
label
confidence
flagCount
createdAt

🎮 Gamification Overview
🟢 +10 points → High confidence predictions (>70%)
🟡 +5 points → Medium confidence (50–70%)
🔴 -2 points → Incorrect/flagged results
🏆 Badges
Starter Recycler
Sustainability Hero
Eco Helper
Community Leader
Streak Master
🐳 Run Locally (Docker)
docker-compose up --build

---

## 🚀 Getting Started (Local Development)

You need **three services** running: the React frontend, the Express REST API, and the Python AI service.

### Prerequisites

- Node.js 18+
- Python 3.10–3.12 (recommended for the full ML stack; 3.13+ works in mock mode)
- MongoDB — a free [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) cluster works

### 1. Configure environment variables

**Backend API** — edit `backend/base_server/.env.development`:

```env
ENV=development
PORT=3000
SERVER_URL=http://localhost:3000
DATABASE_URL="mongodb+srv://<user>:<password>@<cluster>.mongodb.net/<dbname>"
MIGRATE_MONGO_URI="mongodb://localhost:27017/base"
MIGRATE_AUTOSYNC="true"
SALT_ROUNDS="10"
EMAIL_SERVICE_API_KEY="re_your_resend_key"
ACCESS_TOKEN_SECRET="your-access-secret"
REFRESH_TOKEN_SECRET="your-refresh-secret"
```

> Get a free Resend key at resend.com — or leave it blank if you don't need email verification.

**Frontend** (optional — defaults already match local dev) — create `ai-waste-sort/.env`:

```env
VITE_AI_API_URL=http://localhost:8000
VITE_REST_API_URL=http://localhost:3000/v1
```

### 2. Install dependencies

```bash
# Frontend
cd ai-waste-sort
npm install

# Backend API
cd ../backend/base_server
npm install

# AI service
cd ..
pip install fastapi "uvicorn[standard]" python-multipart \
    opencv-python-headless numpy pillow
# For real model inference (Python <= 3.12):
pip install -r requirements.txt
```

### 3. Run the services (3 terminals)

```bash
# Terminal 1 — Frontend  →  http://localhost:5173
cd ai-waste-sort && npm run dev

# Terminal 2 — REST API  →  http://localhost:3000/v1
cd backend/base_server && npm run dev

# Terminal 3 — AI service  →  http://localhost:8000
cd backend && python -m uvicorn main:app --port 8000 --reload
```

### 4. Test the pipeline

1. Open http://localhost:5173 → sign up / log in
2. Go to **Scan** → upload an image or use the camera
3. Click **Save Scan** → check **History** to confirm it persisted to MongoDB

### Notes

- **Mock mode**: if `waste_detector.pt` is missing or `ultralytics` isn't installed, `/scan` returns simulated detections (random labels, ~95% confidence). Check `http://localhost:8000/health` — `"mode": "mock"` vs `"waste_model"`.
- **Train a model**: `cd backend && python train.py` (uses `data/dataset-resized/`). Output weights go to `backend/` as `waste_detector.pt`.
- Windows alternative: `start-all-services.bat` / `start-all-services.sh` at the repo root.


📅 Development Timeline
Phase	Status
Planning & Research	✅ Completed
Model Development	🔄 In Progress
Backend Development	🔄 In Progress
Frontend Development	🔄 In Progress
Integration & Testing	⏳ Pending

Deployment	⏳ Pending
🔮 Future Enhancements
📱 AR-based real-time waste detection
🔗 Blockchain-based eco reward system
🤖 AI chatbot for recycling guidance
📌 Next Steps
Train and optimize ML model
Connect full pipeline (Frontend → Backend → AI)
Implement gamification system
Deploy MVP version

🤝 Contribution

This project is currently in active development. Contributions, ideas, and feedback are welcome!

📜 License

MIT License

👨‍💻 Author

Faaiz Ahmed
MERN Stack Developer | Exploring AI & Blockchain