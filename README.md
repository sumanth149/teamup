# TeamUp — Next-Gen College Student Collaboration Platform & AI Project Mentor

> **"Build Together. Learn Together. Innovate Together."**  
> TeamUp is a production-grade collaboration ecosystem for college and university students that blends a **student professional network**, a **project workspace & Kanban board**, **real-time chat**, and an **intelligent AI project mentor**.

---

## 🌟 Key Features

1. **Student Professional Network & Profiles**
   - Profile completion gauge (`████████░░ 85%`)
   - College, Branch, Year, Bio, Availability (15+ hrs/wk, 5-15 hrs/wk, Weekends)
   - Skills categorized into Frontend, Backend, AI/ML, DevOps, Design, Database
   - Verified GitHub, LinkedIn, and Portfolio links

2. **Project Creation & Multi-Factor Discovery**
   - Post projects with categories, required roles, technologies, difficulty, and duration
   - Multi-factor search across keywords, branches, categories, status, and difficulties
   - Sorting by newest, most popular, team size, and recently updated

3. **Team Formation & Join Request System**
   - Students apply with custom role preferences and cover pitch
   - Project leads review applicants, compare candidate skills, and 1-click **Accept** or **Reject**
   - Automatically adds accepted students to the project team and dispatches in-app notifications

4. **Dedicated Project Workspace**
   - **Kanban Task Board**: 4-stage lanes (`TODO`, `IN_PROGRESS`, `REVIEW`, `COMPLETED`) with priorities, deadlines, and member assignments
   - **Sprint Progress Meter**: Real-time percentage completion calculation
   - **Task Comments Drawer**: Discussion and deliverable updates per task
   - **Resources Hub**: Documentation, research papers, repository links, and tutorials
   - **Team Chat Room**: Integrated real-time messaging

5. **Real-Time Chat & WebSockets**
   - Powered by Django Channels & ASGI WebSockets
   - 1-to-1 direct peer chats and project team rooms
   - Live typing indicators and instant message delivery

6. **TeamUp AI Project Mentor 🤖**
   - **AI Project Idea Generator**: Generates novel capstone ideas tailored by domain, available student skills, and team size
   - **AI Technology Advisor**: Explains the optimal frontend, backend, database, and cloud stack with engineering justifications
   - **AI Task Breakdown & Board Generator**: 1-click generation of 8-10 phased Kanban tasks directly populated into the workspace board
   - **AI Teammate Recommendations**: Algorithmic match scoring based on required technologies and cross-branch diversity
   - **AI Phased Roadmap Generator**: Phase 1 to Phase 8 milestone timeline
   - **AI Concept Explainer**: Analogies, code snippets, and mini-exercises for CS students

7. **Campus Admin Dashboard & Platform Telemetry**
   - Total students, active projects, and completed tasks metrics
   - Distribution of students by engineering branch
   - Projects by innovation domain and popular technologies breakdown

---

## 🏗️ Architecture & Technology Stack

```
   ┌────────────────────────────────────────────────────────┐
   │                     REACT 19 SPA                       │
   │   Vite + Tailwind CSS v4 + Lucide Icons + Axios Interceptors │
   └───────────────────────────┬────────────────────────────┘
                               │ HTTPS REST & WebSockets (ws://)
                               ▼
   ┌────────────────────────────────────────────────────────┐
   │                 DJANGO 5.0 ASGI SERVER                 │
   │               Daphne + Channels + SimpleJWT            │
   ├───────────────────────────┬────────────────────────────┤
   │  users        projects    │  tasks      chat           │
   │  notifications            │  ai_mentor (TeamUp AI)     │
   └─────────────┬─────────────┴─────────────┬──────────────┘
                 │                           │
                 ▼                           ▼
          SQLite / PostgreSQL         TeamUp AI Synthesizer
                                     (Gemini / OpenAI API + Fallback)
```

---

## 🚀 Quickstart Guide

### 1. Backend Setup

```bash
cd backend

# Run database migrations
python manage.py migrate

# Seed database with realistic students, projects, tasks, and chats
python seed_data.py

# Launch ASGI server with Channels / Daphne
daphne -b 127.0.0.1 -p 8000 config.asgi:application
# or
python manage.py runserver
```

The Django REST API will be available at `http://127.0.0.1:8000/api/`.

### 2. Frontend Setup

```bash
cd frontend

# Install dependencies (already completed)
npm install

# Start development server
npm run dev
```

Visit the app at `http://localhost:5173`.

---

## 🔑 Demo Accounts (Pre-Seeded)

| Name | Email | Password | Branch | Role |
| :--- | :--- | :--- | :--- | :--- |
| **Siva Ramanathan** | `siva@teamup.edu` | `password123` | Computer Science | Project Lead |
| **Ananya Sharma** | `ananya@teamup.edu` | `password123` | Electronics (ECE) | Edge ML & IoT |
| **Rohit Verma** | `rohit@teamup.edu` | `password123` | IT & Design | Frontend / UI |
| **Priya Nair** | `priya@teamup.edu` | `password123` | Data Science & AI | NLP Researcher |
| **Platform Admin** | `admin@teamup.edu` | `adminpassword123`| System Architecture | Administrator |

*(1-click login buttons are also available on the Login page for instant access!)*

---

## 🧪 Running Automated Tests

```bash
cd backend
python manage.py test test_teamup
```
All 6 automated tests verify user auth, profile percentage calculation, project lifecycle, join request approvals, Kanban task progress calculation, and the TeamUp AI tools.
