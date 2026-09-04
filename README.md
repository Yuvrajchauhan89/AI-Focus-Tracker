# 🧠 AI Focus Tracker

> **Real-time AI-powered focus monitoring dashboard for tracking concentration, detecting distractions, and analyzing study/work sessions.**

AI Focus Tracker is a modern full-stack web application designed to help users understand and improve their focus during study or work sessions.

The application uses webcam-based focus metrics, session tracking, analytics, distraction detection, and optional IoT alerts to create a complete focus-monitoring experience.

---

## ✨ Features

### 🎥 Live Focus Tracking

* Real-time webcam interface
* Live focus score
* Focus category detection
* Eye openness monitoring
* Gaze direction tracking
* Head-pose status
* Blink-rate telemetry
* Distraction detection
* Animated AI scanning interface

### 📊 Focus Analytics

* Daily focus statistics
* Average focus score
* Focus percentage
* Total study/session time
* High / medium / low focus breakdown
* Distracted time
* Most focused hour
* Least focused hour
* Hourly focus analysis
* Multi-day focus trends

### 📝 Session Management

* Start focus sessions
* Stop and save sessions
* Session history
* Individual session analytics
* Distraction event tracking
* Historical focus data

### 🚨 Distraction Alerts

When distraction is detected, the application can:

* Display a visual warning
* Play an alert sound
* Send an IoT focus alert
* Record the distraction event

### 🔌 IoT Integration

The backend provides endpoints for:

* Registering IoT devices
* Checking device status
* Sending distraction alerts
* Recording alert history

### ⚙️ Settings

Configurable options include:

* Sound alerts
* IoT alerts
* IoT device configuration
* Focus tracking preferences

---

## 🖥️ Interface

The application includes:

* 🏠 Home dashboard
* 📡 Live Tracker
* 📈 Analytics Dashboard
* 🕐 Session History
* ⚙️ Settings

The UI uses a futuristic glassmorphism / cyber-style design with animated elements and responsive layouts.

---

## 🏗️ Tech Stack

### Frontend

* **React**
* **TypeScript**
* **Vite**
* **Tailwind CSS**
* **Framer Motion**
* **Recharts**
* **React Webcam**
* **Lucide Icons**
* **React Query**
* **Wouter**

### Backend

* **Node.js**
* **Express**
* **TypeScript**
* **Drizzle ORM**
* **Zod**

### Database

The project uses a database layer powered by:

* PostgreSQL
* Drizzle ORM
* Drizzle schema/type definitions

### Architecture

```text
┌───────────────────────────────┐
│        React Frontend         │
│                               │
│  Dashboard • Live Tracker     │
│  History • Analytics          │
│  Settings                     │
└───────────────┬───────────────┘
                │
                │ REST API
                ▼
┌───────────────────────────────┐
│       Express API Server      │
│                               │
│ Sessions • Focus • Analytics  │
│ IoT • Health                  │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│       PostgreSQL Database     │
│                               │
│ Sessions                      │
│ Focus Data                    │
│ IoT Alerts                    │
└───────────────────────────────┘
```

---

## 🧠 Focus Detection

The focus engine maintains:

* A frame queue
* A sliding score window
* Focus score smoothing
* Distraction timers
* Focus categories

Focus states are classified into:

| Score                 | State           |
| --------------------- | --------------- |
| 80–100                | 🟢 High Focus   |
| 50–79                 | 🟡 Medium Focus |
| 30–49                 | 🟠 Low Focus    |
| Distraction condition | 🔴 Distracted   |

The system also considers:

* Eye openness
* Gaze direction
* Head pose
* Blink rate
* Focus score history

### ⚠️ Current ML Implementation

The current repository contains a **simulated focus-data generator** for reliable demonstration and UI development.

The architecture is designed so that the simulation can later be replaced with a real computer-vision pipeline such as:

```text
Webcam
   ↓
Face Detection
   ↓
Eye / Gaze Detection
   ↓
Head Pose Estimation
   ↓
Focus Score
   ↓
Distraction Detection
   ↓
Analytics + Alerts
```

---

## 📁 Project Structure

```text
ai-focus-tracker/
│
├── artifacts/
│   │
│   ├── api-server/
│   │   └── src/
│   │       ├── routes/
│   │       │   ├── analytics.ts
│   │       │   ├── focus.ts
│   │       │   ├── health.ts
│   │       │   ├── iot.ts
│   │       │   └── sessions.ts
│   │       └── ...
│   │
│   └── focus-tracker/
│       ├── src/
│       │   ├── components/
│       │   ├── hooks/
│       │   ├── pages/
│       │   │   ├── dashboard.tsx
│       │   │   ├── history.tsx
│       │   │   ├── home.tsx
│       │   │   ├── live-tracker.tsx
│       │   │   └── settings.tsx
│       │   └── ...
│       └── ...
│
├── lib/
│   ├── db/
│   │   └── src/
│   │       └── schema/
│   │
│   └── api-spec/
│
├── package.json
├── pnpm-workspace.yaml
├── tsconfig.json
└── replit.md
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/ai-focus-tracker.git

cd ai-focus-tracker
```

### 2. Install dependencies

This project uses **pnpm**.

```bash
pnpm install
```

If you don't have pnpm:

```bash
npm install -g pnpm
```

### 3. Configure the database

Create the required environment configuration for your PostgreSQL database.

Example:

```env
DATABASE_URL=postgresql://username:password@localhost:5432/focus_tracker
```

Make sure your PostgreSQL database is running.

### 4. Start the application

Start the frontend:

```bash
cd artifacts/focus-tracker
pnpm dev
```

The Vite development server will start locally.

Start the API server according to the server configuration in:

```text
artifacts/api-server/
```

---

## 🔌 API Endpoints

### Sessions

```http
GET    /sessions
POST   /sessions
GET    /sessions/:id
PATCH  /sessions/:id
```

### Focus Data

```http
POST /focus/record
```

### Analytics

```http
GET /analytics/daily
GET /analytics/trends
```

### IoT

```http
POST /iot/focus-alert
GET  /iot/status
POST /iot/register
```

### Health

```http
GET /health
```

---

## 📈 Example Focus Data

A focus data point contains information such as:

```json
{
  "focusScore": 87,
  "focusCategory": "HIGH_FOCUS",
  "eyeOpenness": 0.92,
  "gazeDirection": "CENTER",
  "blinkRate": 12,
  "headPose": "FORWARD",
  "isDistraction": false
}
```

---

## 🔮 Future Improvements

The project can be extended with:

* [ ] Real MediaPipe Face Mesh integration
* [ ] Real gaze estimation
* [ ] Real head-pose estimation
* [ ] Blink detection using facial landmarks
* [ ] ML-based focus classification
* [ ] User authentication
* [ ] Cloud deployment
* [ ] Mobile application
* [ ] Personalized focus models
* [ ] Productivity recommendations
* [ ] AI-generated study reports
* [ ] Smart notifications
* [ ] Physical IoT distraction device
* [ ] ESP32 integration
* [ ] Advanced productivity analytics

---

## 🎯 Use Cases

AI Focus Tracker can be used for:

* 📚 Student study sessions
* 💻 Remote workers
* 👨‍💻 Programmers
* 🧑‍🎓 Exam preparation
* 🧠 Productivity experiments
* 🏢 Workplace focus analysis
* 🔬 Human-computer interaction research

---

## 🔐 Privacy

The application is designed around webcam-based focus monitoring.

If real computer-vision processing is added, a recommended production architecture is to process webcam frames **locally on the user's device** whenever possible instead of uploading raw video to a server.

> Do not use focus metrics as a high-stakes assessment of a person's performance, mental state, or abilities.

---

## 🛠️ Development

Run type checking:

```bash
pnpm typecheck
```

Build the project:

```bash
pnpm build
```

Frontend development:

```bash
cd artifacts/focus-tracker
pnpm dev
```

Frontend production build:

```bash
pnpm build
```

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch

```bash
git checkout -b feature/amazing-feature
```

3. Make your changes
4. Commit your changes

```bash
git commit -m "Add amazing feature"
```

5. Push the branch

```bash
git push origin feature/amazing-feature
```

6. Open a Pull Request

---

## 📜 License

This project is licensed under the **MIT License**.

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.

---

### Built with ❤️ and a lot of caffeine ☕
