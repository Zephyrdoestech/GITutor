# GITutor: AI-Powered Adaptive Programming Micro-Tutor

## Project Summary

**GITutor** is a web-based personalized programming learning platform designed to support beginner and intermediate programming students. It combines structured programming lessons, GitHub-based coding exercises, automated test result tracking, student progress monitoring, adaptive learning, and personalized practice recommendations.

The core learning flow is:

```
Learn → Practice in GitHub → Test → Track Progress → Identify Weaknesses → Recommend Practice
```

GITutor uses GitHub as the exercise delivery platform, allowing students to practice in realistic development environments. Automated test results from GitHub are collected and analyzed to monitor student performance and guide what each student should work on next.

AI-powered programming assistance is included as an optional supporting layer — helping students understand errors and ask programming questions — but it does not replace the core curriculum, exercises, and progress tracking system.

---

## Problem

Beginner programming students commonly face the following challenges:

- **Difficulty applying concepts in realistic environments** — Understanding theory does not always translate to writing actual code in a development environment.
- **Static, non-adaptive exercises** — Traditional coding exercises do not adjust to a student's specific weaknesses, meaning a struggling student receives the same material as a high-performing student.
- **Repeated mistakes** — Without targeted feedback, students may repeat the same errors across multiple exercises without understanding why.
- **Limited instructor visibility** — Instructors may have difficulty monitoring the individual progress of many students and identifying who is struggling and on which topics.
- **No systematic identification of learning gaps** — Neither students nor instructors may have a clear picture of which concepts need more practice.

---

## Target Users

**Primary Users:**

- **Students** — Beginner and intermediate programming learners who want to improve their programming skills through structured lessons and practical exercises.
- **Instructors/Teachers** — Programming instructors who want to monitor student progress, identify learning gaps, and provide more targeted support.

---

## Proposed Solution

GITutor addresses the above problems through the following approach:

- **Interactive curriculum** — A structured roadmap of programming topics guides students through lessons in a logical sequence.
- **GitHub-based exercises** — Programming exercises are linked to GitHub repositories, giving students practice in realistic coding environments.
- **Automated test verification** — Test results from GitHub exercises are recorded, providing objective evidence of exercise completion and correctness.
- **Progress tracking** — Student scores, completed exercises, and topic progress are tracked over time.
- **Diagnostic assessment** — An initial assessment identifies a student's existing knowledge and gaps before they begin the curriculum.
- **Personalized recommendations** — The system analyzes weak areas and suggests targeted practice activities.
- **Instructor monitoring** — Instructors can view student progress, identify difficult topics, and monitor class performance at a glance.
- **Optional AI programming assistance** — Students can ask the AI tutor programming questions or submit error messages for beginner-friendly explanations.

---

## Project Features

### AUTH — Authentication & User Management

#### AUTH-01 — User Authentication
> **Priority:** Must-Have

- Students and instructors can securely log in to GITutor.
- Invalid credentials produce an appropriate error message.
- After login, users are directed to the appropriate area based on their role.

#### AUTH-02 — Role-Based Access
> **Priority:** Must-Have

- The system distinguishes between student and instructor roles.
- Students and instructors each receive access to the features appropriate to their role.
- Unauthorized users cannot access restricted areas.

---

### CURR — Curriculum & Learning

#### CURR-01 — Interactive Curriculum Roadmap
> **Priority:** Must-Have

- Students can view a roadmap of programming topics and lessons.
- The roadmap displays learning progress and highlights completed topics.

#### CURR-02 — Programming Lessons & Exercises
> **Priority:** Must-Have

- Students can access lesson material and associated programming exercises.
- Exercise completion can be recorded and reflected in progress tracking.

---

### GITHUB — GitHub Exercises & Testing

#### GITHUB-01 — GitHub Repository Integration
> **Priority:** Must-Have

- Programming exercises are associated with GitHub repositories.
- Students can access exercise repository information from within GITutor.

#### GITHUB-02 — Exercise Test Result Tracking
> **Priority:** Must-Have

- Test results from GitHub exercises can be recorded in the system.
- Pass/fail results are associated with the appropriate student and exercise.
- Results contribute to overall progress tracking.

---

### PROG — Progress & Performance

#### PROG-01 — Student Progress Dashboard
> **Priority:** Must-Have

- Students can view their completed activities, scores, and topic progress.
- The dashboard highlights areas that require improvement.

#### PROG-02 — Instructor Progress Dashboard
> **Priority:** Must-Have

- Instructors can monitor student progress across topics.
- Instructors can identify topics that students commonly find difficult.
- Instructors can view performance by student and by topic.

---

### ADAPT — Assessment & Recommendations

#### ADAPT-01 — Diagnostic Assessment
> **Priority:** Should-Have

- Students can take an initial diagnostic assessment before beginning the curriculum.
- Assessment results are mapped to relevant programming topics.
- Results are stored for use in personalized recommendations.

#### ADAPT-02 — Personalized Practice Recommendations
> **Priority:** Should-Have

- The system analyzes student performance data to identify weak topics.
- The system recommends appropriate practice activities based on identified weaknesses.

---

### AI — AI Micro-Tutor

#### AI-01 — AI Programming Assistant
> **Priority:** Nice-to-Have

- Students can ask programming-related questions to the AI tutor.
- The AI provides beginner-friendly explanations.
- Responses consider the student's current learning context when possible.

#### AI-02 — AI Error Explanation
> **Priority:** Nice-to-Have

- Students can submit programming errors or test errors to the AI.
- The AI explains the error in understandable language.
- The AI can suggest the relevant concept or the next recommended learning step.

---

## MoSCoW Priority Summary

| Priority | Feature IDs |
|---|---|
| **Must-Have** | AUTH-01, AUTH-02, CURR-01, CURR-02, GITHUB-01, GITHUB-02, PROG-01, PROG-02 |
| **Should-Have** | ADAPT-01, ADAPT-02 |
| **Nice-to-Have** | AI-01, AI-02 |

> **Note:** AUTH-01 and AUTH-02 are supporting implementation modules derived from the need for student/instructor users and role-based functionality. They are not features explicitly listed in the original project proposal title but are necessary for the system to function correctly.

---

## MVP Scope

The initial **Minimum Viable Product (MVP)** will prioritize the **eight Must-Have features**:

- AUTH-01, AUTH-02 — Authentication and role-based access
- CURR-01, CURR-02 — Curriculum roadmap and lessons
- GITHUB-01, GITHUB-02 — GitHub exercise integration and test tracking
- PROG-01, PROG-02 — Student and instructor dashboards

The **Should-Have features** (ADAPT-01, ADAPT-02) are planned for the next development stage after the MVP is functional.

The **Nice-to-Have AI features** (AI-01, AI-02) are optional enhancements and should not block development of the core learning system.

---

## Technology Stack

Technology stack: **To be finalized.**

> Setup instructions will be updated after the technology stack is selected and agreed upon by the team.

---

## Team

**Project:** GITutor: AI-Powered Adaptive Programming Micro-Tutor

**Team:** The Recocious (DarRikuSyos)

| # | Member |
|---|---|
| 1 | Darryll B. Eral |
| 2 | Ricksmer F. Cabatingan |
| 3 | Precious Ann S. Tolentino |

> Individual roles are to be finalized. See [`docs/team-roles.md`](docs/team-roles.md) for details.

---

## Setup

Setup instructions will be updated after the technology stack is finalized.

---

## Project Management

**ClickUp Workspace:**
[INSERT CLICKUP WORKSPACE URL]

> Please update this link once the ClickUp workspace has been created.

---

## Development Workflow

Each task follows this traceability chain:

```
ClickUp Task
    → GitHub Issue
    → Feature/Fix Branch
    → Commit
    → Pull Request
    → Peer Review
    → Testing/Verification
    → Done
```

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for full branch naming conventions, commit format guidelines, and pull request rules.
