# DNATE MSL Practice Gym — 🏆 1st Place, MGEN (now SEIS) Hackathon 2025

**AI-driven Practice & Performance Dashboard for Medical Science Liaisons**

Built from scratch in 48 hours at the **MGEN (now SEIS) Hackathon 2025, Northeastern University** (Oct 15–17, 2025), in partnership with **DNATE** — and **winner of 1st place** against 10+ competing teams.

**🔗 Live demo:** https://msl-practice-gym-oats.vercel.app

## 🏆 The Hackathon

Medical Science Liaisons (MSLs) need to stay current with vast amounts of medical literature and communicate complex scientific information to healthcare providers (HCPs). MSLs spend weeks preparing for each HCP interaction, manually reviewing hundreds of documents — with no efficient way to practice scenarios and receive immediate, actionable feedback on their communication skills.

In 48 hours, our 4-person team of Northeastern University graduate students built a full-stack AI practice platform that solves this:

- 🗣️ Practice real-world question scenarios with dynamic HCP personas
- 🤖 AI coach with real-time feedback scoring on scientific accuracy, communication clarity, and engagement
- 📊 Interactive dashboards tracking confidence and category trends
- 📈 Performance analytics by persona and communication category
- 📚 Expert sample responses based on STAR, LEAP, CAR frameworks
- 🔒 Secure auth and personal progress tracking

| Result | |
|---|---|
| 🥇 Placement | **1st Place — DNATE Challenge Winner** |
| ⏱️ Build time | 48 hours, from scratch |
| 🏁 Competition | 10+ teams |
| 🎯 Retrieval accuracy | 90% in document retrieval |

### In the News

- [MGEN Hackathon announcement (LinkedIn)](https://www.linkedin.com/posts/mgenhackathon-graduateengineering-innovation-share-7382431912989970432-ep24/)
- [Debbie Steiner Hayes on the hackathon (LinkedIn)](https://www.linkedin.com/posts/debbie-steiner-hayes_hackathon-ai-innovation-ugcPost-7385722528599822336-_jB6/)
- ["And we have a winner!" — Stuart Paap (LinkedIn)](https://www.linkedin.com/posts/stuart-paap_and-we-have-a-winner-in-just-48-hours-ugcPost-7385090667728809984-aBri)

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 19, Vite, Tailwind CSS |
| **Backend** | Node.js, Express.js |
| **AI Coach** | OpenAI API |
| **Database** | PostgreSQL |
| **API Auth** | JWT (JSON Web Token) |
| **Charts** | Recharts |
| **Icons** | Lucide React |
| **Styling** | Tailwind + Custom DNATE Theme |

## 🚢 Deployment

| Component | Platform | Purpose |
|-----------|----------|---------|
| **Frontend** | Vercel | React application hosting |
| **Backend** | Railway | Node.js API server |
| **Database** | Supabase | PostgreSQL database |

## 📁 Repository Structure

```
MGEN-Hackathon-2025/
│
├── frontend/                 # React 19 + Vite + Tailwind app
│   ├── src/
│   │   ├── components/       # NavBar, ChatSession, SttButton
│   │   ├── pages/            # Dashboard, Personas, Sessions, Auth, ...
│   │   └── services/         # API clients (axios)
│   └── public/
│
├── server/                   # Node.js / Express API
│   └── src/
│       ├── routes/           # auth, sessions, personas, analytics, ...
│       ├── services/         # aiCoach (OpenAI-powered feedback)
│       ├── middleware/       # JWT validation
│       └── db/               # PostgreSQL config
│
├── docs/
│   └── challenge/            # Original hackathon challenge materials
│       ├── DNATE MSL Practice Gym Hackathon.docx
│       ├── personas.json
│       ├── questions.json
│       └── schema.sql
│
└── README.md
```

## ⚙️ Environment Variables

### Backend (`/server/.env`)
```env
PORT=5000
DATABASE_URL=postgresql://<USER>:<PASSWORD>@localhost:5432/dnate_db
JWT_SECRET=<your_jwt_secret>
OPENAI_API_KEY=<your_openai_key>
```

### Frontend (`/frontend/.env`)
```env
VITE_API_URL=http://localhost:5000/api
```

## 🚀 Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/MGEN-Hackathon-2025.git
cd MGEN-Hackathon-2025
```

### 2. Backend Setup
```bash
cd server
npm install
```

Create `.env` (see above), then initialize the database using `docs/challenge/schema.sql`:
```sql
CREATE DATABASE dnate_db;
```

Start the server:
```bash
npm run dev
```
Backend runs at `http://localhost:5000`

### 3. Frontend Setup
```bash
cd ../frontend
npm install
npm start
```
Frontend runs at `http://localhost:5173`

## ✨ Key Features

### 📊 Dashboard
- View total sessions, streaks, and confidence heatmaps
- Analyze category-based confidence via interactive charts
- Visualize confidence trends (1m, 3m, 6m views)

### 👥 Personas
- Browse personas (Oncologist, Cardiologist, Neurologist)
- Explore communication style, motivations, and question patterns
- Launch practice sessions from a persona profile

### 🗣️ Practice Sessions
- Live chat sessions against AI-simulated HCP personas
- Speech-to-text input for realistic verbal practice
- AI coach feedback on every response

### 👤 Profile Page
- Manage profile and organization details
- Change password securely
- Track performance metrics by category and persona

### 📝 Sample Responses
- Expert-crafted responses using STAR, CAR, LEAP frameworks
- Key talking points and structured reasoning
- Compare your answers with expert examples

## 🔐 Authentication Flow

1. Login via `/auth/login`
2. JWT stored in `localStorage`
3. Axios interceptor attaches token to requests
4. Backend validates token on protected routes

## 📡 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Log in and receive JWT |
| `GET` | `/api/auth/me` | Fetch logged-in user details |
| `PATCH` | `/api/auth/me` | Update user profile |
| `POST` | `/api/auth/change-password` | Update user password |

### Sessions
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/sessions` | Get all user sessions |
| `POST` | `/api/sessions` | Create new session |
| `PATCH` | `/api/sessions/:id/complete` | Mark a session as completed |
| `GET` | `/api/sessions/stats` | Retrieve dashboard statistics |

### Personas
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/personas` | Get all personas |
| `GET` | `/api/personas/:id` | Get persona details |

## 🗄️ Database Schema

The full PostgreSQL schema (users, personas, questions, sessions, responses, analytics) is in [`docs/challenge/schema.sql`](docs/challenge/schema.sql).

## 🎨 DNATE Brand Design System

| Element | Value |
|---------|-------|
| **Primary Blue** | `#0375E9` |
| **Indigo Base** | `#18202D` |
| **Graphite Text** | `#505A69` |
| **Gray Accent** | `#F5F7FB` |
| **Font (Sans)** | Manrope |
| **Font (Serif)** | Domine |

## 🔮 Future Enhancements

- 📄 Export reports and summaries as PDF
- 🔔 Session reminders and progress gamification
- 👮 Role-based access (Admin, Trainer, MSL)
- 🎙️ Voice-based persona simulation

## 💡 Key Learnings

This hackathon reinforced the power of retrieval-augmented, domain-specific AI. The key insight was that MSLs don't need generic AI — they need AI that understands their specific document corpus and can provide contextually relevant practice scenarios.

## 👥 Team — Northeastern University

- Aravind Balaji
- Guhan Santhanam SP
- Thejus Thomson
- Ashmiya VijayaChandran

Challenge sponsored by the **DNATE Engineering Team**.

## 📄 License

This project was built for the DNATE challenge at the MGEN (now SEIS) Hackathon 2025, Northeastern University.
