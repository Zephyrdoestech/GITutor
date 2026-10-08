# GITutor — High-Level Architecture

**Project:** GITutor: AI-Powered Adaptive Programming Micro-Tutor  
**Team:** The Recocious (DarRikuSyos)  
**Version:** 1.0 — Initial Draft  
**Status:** Conceptual — Implementation details TBD

---

> **Note:** This document describes the intended high-level architecture for GITutor. The technology stack has not yet been finalized. All implementation choices marked **TBD** will be updated after the team has agreed on specific technologies.

---

## Conceptual Overview

GITutor is a web-based platform that connects students and instructors through a structured learning system built around GitHub-based exercises and automated test tracking.

```
┌─────────────────────────────────────────────────────────────┐
│                        Users                                │
│              Student / Instructor                           │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                      Frontend                               │
│  - Curriculum Roadmap        - Student Progress Dashboard   │
│  - Lesson & Exercise Views   - Instructor Dashboard         │
│  - Diagnostic Assessment     - AI Tutor Chat (optional)     │
│  - Login / Role-Based UI                                    │
│                                                             │
│  Implementation: TBD                                        │
└────────────────────────┬────────────────────────────────────┘
                         │  HTTP / REST or GraphQL
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                    Backend / API                             │
│  - Authentication & Session Management                      │
│  - Role-Based Access Control                                │
│  - Curriculum & Lesson Logic                                │
│  - Exercise Management                                      │
│  - Progress Calculation                                     │
│  - Recommendation Engine                                    │
│  - GitHub Integration Handling                              │
│  - AI Tutor API Proxy (optional)                            │
│                                                             │
│  Implementation: TBD                                        │
└──────────────┬────────────────────────┬─────────────────────┘
               │                        │
               ▼                        ▼
┌──────────────────────┐    ┌───────────────────────────────┐
│      Database         │    │       External Services       │
│                      │    │                               │
│  - Users             │    │  GitHub API / Repositories    │
│  - Roles             │    │  (Exercise repos, test runs)  │
│  - Curriculum        │    │                               │
│  - Lessons           │    │  AI / LLM API (optional)      │
│  - Exercises         │    │  (Programming assistant)      │
│  - Test Results      │    │                               │
│  - Progress Records  │    └───────────────────────────────┘
│  - Assessments       │
│  - Recommendations   │
│                      │
│  Implementation: TBD │
└──────────────────────┘
```

---

## Component Descriptions

### 1. Frontend

The frontend is the web interface that students and instructors interact with. It includes:

- **Login / Authentication UI** — Form for user login; redirects based on role.
- **Curriculum Roadmap** — Visual map of programming topics and learning progress.
- **Lesson & Exercise Views** — Content for individual lessons and exercise instructions.
- **Student Progress Dashboard** — Scores, completed activities, and improvement areas.
- **Instructor Dashboard** — Student progress overview, topic performance analysis.
- **Diagnostic Assessment UI** — Quiz/assessment interface for initial evaluation.
- **AI Tutor Chat UI** *(optional)* — Chat interface for AI programming questions.

**Technology:** TBD

---

### 2. Backend / API

The backend handles business logic, data processing, and serves the frontend via an API. It includes:

- **Authentication Service** — Validates credentials, issues sessions/tokens, enforces role access.
- **Curriculum Service** — Manages topics, lessons, and exercise data.
- **GitHub Integration Service** — Connects exercises to GitHub repositories; receives test results.
- **Progress Service** — Aggregates test results and lesson completions into progress records.
- **Assessment Service** — Delivers diagnostic assessments and stores results.
- **Recommendation Engine** — Analyzes weak areas and generates practice recommendations.
- **AI Proxy** *(optional)* — Forwards student questions/errors to the AI/LLM API and returns responses.

**Technology:** TBD

---

### 3. Database

The database stores all persistent application data:

| Data | Description |
|---|---|
| Users | Account credentials, roles (student/instructor) |
| Curriculum | Topics, lessons, learning sequence |
| Exercises | Exercise definitions, GitHub repository links |
| Test Results | Pass/fail results per student per exercise |
| Progress Records | Aggregated progress per student per topic |
| Assessments | Diagnostic questions, student responses, results |
| Recommendations | Generated recommendations per student |

**Technology:** TBD

---

### 4. Authentication

Authentication protects all routes and enforces role-based access:

```
User submits credentials
        ↓
Backend validates credentials
        ↓
Role determined (student / instructor)
        ↓
Session or token issued
        ↓
Frontend redirects based on role
        ↓
All protected API calls verified against session/token
```

**Technology:** TBD (session-based or JWT-based)

---

### 5. Curriculum & Lesson System

The curriculum system organizes learning content:

```
Topic (e.g., "Variables and Data Types")
    └── Lesson (e.g., "What is a Variable?")
            └── Exercise (linked to GitHub repository)
```

Students progress through topics in sequence, unlocking new topics as they complete prerequisites.

---

### 6. GitHub Integration

GitHub serves as the exercise delivery and testing platform:

```
Instructor creates exercise repository on GitHub
        ↓
Exercise linked to GITutor lesson (GITHUB-01)
        ↓
Student forks/accesses repository
        ↓
Student writes code and pushes
        ↓
GitHub Actions runs automated tests
        ↓
Test results sent to GITutor (GITHUB-02)
        ↓
Results stored in database
```

**Integration method:** TBD (GitHub API, GitHub Actions webhooks, or manual result entry)

---

### 7. Exercise & Test Result Tracking

Test results flow from GitHub into the GITutor system:

```
GitHub test result (pass / fail)
        ↓
GITutor Backend receives result
        ↓
Stored in Test Results table (student + exercise)
        ↓
Progress Service updates student progress
```

---

### 8. Student Progress Tracking

Progress is calculated from lesson completions and test results:

```
Lesson completed + Exercise passed
        ↓
Progress Record updated (topic % complete)
        ↓
Student Dashboard refreshed (PROG-01)
        ↓
Instructor Dashboard refreshed (PROG-02)
```

---

### 9. Diagnostic Assessment

The initial assessment identifies knowledge gaps before the curriculum begins:

```
Student takes diagnostic quiz
        ↓
Responses stored in database
        ↓
Results mapped to curriculum topics
        ↓
Weak topics identified
        ↓
Recommendations generated (ADAPT-02)
```

---

### 10. Recommendation & Adaptive Learning System

The recommendation engine analyzes performance data to suggest practice:

```
Progress Data + Assessment Results
        ↓
Weak Topics Identified
        ↓
Recommendation Engine selects relevant exercises
        ↓
Recommendations presented to student (ADAPT-02)
        ↓
Updated as new results arrive
```

---

### 11. Instructor Dashboard

The instructor dashboard aggregates student data for monitoring:

```
All Student Progress Records
        ↓
Aggregated by Topic
        ↓
Instructor Dashboard (PROG-02)
        ↓
Instructor can view: individual student progress,
topic-level pass rates, students needing support
```

---

### 12. AI Programming Tutor *(Optional)*

The AI tutor is an optional supporting layer:

```
Student types question or pastes error (AI-01 / AI-02)
        ↓
Frontend sends to Backend AI Proxy
        ↓
Backend forwards to AI/LLM API
        ↓
Response returned and displayed to student
```

The AI tutor does **not** replace the curriculum or exercise system. It supplements student learning by explaining concepts and errors in beginner-friendly language.

**AI/LLM Provider:** TBD

---

## Data Flow Summary

```
Student/Instructor
      ↓
  Frontend (TBD)
      ↓ REST/GraphQL API
  Backend / API (TBD)
      ↓                      ↓                    ↓
  Database (TBD)      GitHub (Exercises,     AI/LLM API (TBD)
                       Test Results)         [Optional]
```

---

## Security Considerations

- All routes must be protected by authentication.
- Role-based access control must be enforced at the API level (not only the frontend).
- Environment variables must store all secrets (API keys, DB credentials). See `.env.example`.
- HTTPS should be enforced in production.
- GitHub webhook secrets should be validated before processing payloads.

---

## Future Architecture Considerations

The following components may be considered in later development stages but are **not in scope for the MVP**:

- In-browser code editor or terminal
- Internal Git hosting
- Plagiarism detection
- Gamification / leaderboards
- LMS (Learning Management System) integration
