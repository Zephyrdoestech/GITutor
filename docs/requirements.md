# GITutor Requirements

**Project:** GITutor: AI-Powered Adaptive Programming Micro-Tutor  
**Team:** The Recocious (DarRikuSyos)  
**Version:** 1.0 — Initial Draft

---

## Overview

This document defines the functional requirements for GITutor. Each requirement is organized by feature group and includes a feature ID, user story, MoSCoW priority, acceptance criteria, and dependencies.

---

## Feature Groups

| Group | Code | Description |
|---|---|---|
| Authentication & User Management | AUTH | Login and role-based access |
| Curriculum & Learning | CURR | Roadmap, lessons, and exercises |
| GitHub Exercises & Testing | GITHUB | Repository integration and test results |
| Progress & Performance | PROG | Student and instructor dashboards |
| Assessment & Recommendations | ADAPT | Diagnostic assessment and recommendations |
| AI Micro-Tutor | AI | AI programming assistant and error explanation |

---

## AUTH — Authentication & User Management

### AUTH-01 — User Authentication

**Priority:** Must-Have

**User Story:**  
As a student or instructor, I want to securely log in so that I can access the appropriate features of GITutor.

**Acceptance Criteria:**
- A valid user can successfully log in using their credentials.
- Invalid credentials produce a clear and appropriate error message.
- The user's role (student or instructor) is recognized after login.
- The user is redirected to the appropriate area based on their role.
- Protected pages cannot be accessed without authentication.
- A logged-in session is maintained appropriately.

**Dependencies:**
- User account data (stored in the database)
- Authentication mechanism (session or token-based)

---

### AUTH-02 — Role-Based Access

**Priority:** Must-Have

**User Story:**  
As a system administrator or instructor, I want the system to distinguish between student and instructor roles so that each user can only access features appropriate to their role.

**Acceptance Criteria:**
- Students can access student-facing features (curriculum, exercises, progress dashboard).
- Instructors can access instructor-facing features (student monitoring, class performance).
- Students cannot access instructor-only areas.
- Instructors cannot be mistakenly given student-only restrictions.
- Unauthorized or unauthenticated users are denied access to protected routes.

**Dependencies:**
- AUTH-01 (User Authentication)
- Role data associated with each user account

---

## CURR — Curriculum & Learning

### CURR-01 — Interactive Curriculum Roadmap

**Priority:** Must-Have

**User Story:**  
As a student, I want to view a structured roadmap of programming topics and lessons so that I can understand what I need to learn and track my overall progress.

**Acceptance Criteria:**
- The student can view a list of programming topics organized in a logical learning sequence.
- Each topic shows its completion status (completed, in progress, not started).
- The roadmap clearly indicates which topics are unlocked and available.
- The student's progress is reflected accurately on the roadmap.

**Dependencies:**
- AUTH-01 (User Authentication)
- AUTH-02 (Role-Based Access — student role)
- Curriculum data (topics and lesson structure in the database)

---

### CURR-02 — Programming Lessons & Exercises

**Priority:** Must-Have

**User Story:**  
As a student, I want to access lesson material and associated programming exercises so that I can learn concepts and practice applying them.

**Acceptance Criteria:**
- The student can open a lesson and read the lesson content.
- Each lesson has at least one associated programming exercise.
- The student can access the exercise associated with a lesson.
- Exercise completion can be recorded and reflected in progress tracking.
- Completed lessons/exercises are visually distinguished from incomplete ones.

**Dependencies:**
- AUTH-01 (User Authentication)
- CURR-01 (Interactive Curriculum Roadmap)
- Lesson and exercise data in the database
- GITHUB-01 (for GitHub-linked exercises)

---

## GITHUB — GitHub Exercises & Testing

### GITHUB-01 — GitHub Repository Integration

**Priority:** Must-Have

**User Story:**  
As a student, I want programming exercises to be linked to GitHub repositories so that I can practice coding in a realistic development environment.

**Acceptance Criteria:**
- Each exercise has an associated GitHub repository or repository link.
- The student can view the repository link or access it from within GITutor.
- The association between an exercise and its GitHub repository is stored correctly.
- The system correctly identifies which student or exercise a repository belongs to.

**Dependencies:**
- CURR-02 (Programming Lessons & Exercises)
- GitHub account and repository access
- GitHub API or repository URL management

---

### GITHUB-02 — Exercise Test Result Tracking

**Priority:** Must-Have

**User Story:**  
As a student, I want my programming exercise test results to be tracked so that the system knows whether I have passed or failed an exercise.

**Acceptance Criteria:**
- Test results (pass/fail) from GitHub exercises can be recorded in the system.
- Results are associated with the correct student and the correct exercise.
- Pass/fail results are stored accurately.
- Results are reflected in student progress tracking (PROG-01).
- Historical test results can be retrieved.

**Dependencies:**
- GITHUB-01 (GitHub Repository Integration)
- PROG-01 (Student Progress Dashboard)
- GitHub Actions or equivalent test automation

---

## PROG — Progress & Performance

### PROG-01 — Student Progress Dashboard

**Priority:** Must-Have

**User Story:**  
As a student, I want to view my progress dashboard so that I can see what I have completed, how I am performing, and where I need to improve.

**Acceptance Criteria:**
- The student can view a list of completed lessons and exercises.
- The student can see scores or pass/fail results per exercise.
- The student can see their progress per topic.
- The dashboard highlights topics or exercises that require improvement.
- Progress data is accurate and up to date.

**Dependencies:**
- AUTH-01 (User Authentication)
- AUTH-02 (Role-Based Access — student role)
- CURR-02 (Programming Lessons & Exercises)
- GITHUB-02 (Exercise Test Result Tracking)

---

### PROG-02 — Instructor Progress Dashboard

**Priority:** Must-Have

**User Story:**  
As an instructor, I want to view a dashboard of student progress so that I can monitor how individual students are performing and identify topics that are commonly difficult.

**Acceptance Criteria:**
- The instructor can view a list of students and their overall progress.
- The instructor can view performance per student per topic.
- The instructor can identify which topics have low pass rates.
- The instructor can filter or sort performance data.
- Data is accurate and reflects the latest test results.

**Dependencies:**
- AUTH-01 (User Authentication)
- AUTH-02 (Role-Based Access — instructor role)
- PROG-01 (Student Progress Dashboard — underlying data)
- GITHUB-02 (Exercise Test Result Tracking)

---

## ADAPT — Assessment & Recommendations

### ADAPT-01 — Diagnostic Assessment

**Priority:** Should-Have

**User Story:**  
As a student, I want to take an initial diagnostic assessment so that the system can understand my existing knowledge and identify gaps before I start the curriculum.

**Acceptance Criteria:**
- The student can access and complete an initial diagnostic assessment.
- Assessment questions are mapped to specific programming topics.
- Assessment results are stored and associated with the student.
- Results are available for use in generating personalized recommendations (ADAPT-02).
- The assessment can only be taken once (or the first submission is used for recommendations).

**Dependencies:**
- AUTH-01 (User Authentication)
- AUTH-02 (Role-Based Access — student role)
- Assessment question data and topic mapping in the database
- ADAPT-02 (Personalized Practice Recommendations — consumes assessment results)

---

### ADAPT-02 — Personalized Practice Recommendations

**Priority:** Should-Have

**User Story:**  
As a student, I want the system to recommend practice activities based on my performance and weaknesses so that I can focus on the areas where I need the most improvement.

**Acceptance Criteria:**
- The system analyzes the student's performance data and assessment results.
- Weak topics are identified based on low scores or failed exercises.
- The system presents a set of recommended practice activities relevant to the identified weaknesses.
- Recommendations are updated when new test results or assessment data are available.
- Recommendations are clearly presented to the student.

**Dependencies:**
- ADAPT-01 (Diagnostic Assessment)
- PROG-01 (Student Progress Dashboard — performance data)
- GITHUB-02 (Exercise Test Result Tracking — test result data)
- Curriculum and exercise data for recommendation mapping

---

## AI — AI Micro-Tutor

### AI-01 — AI Programming Assistant

**Priority:** Nice-to-Have

**User Story:**  
As a student, I want to ask programming-related questions to an AI tutor so that I can get beginner-friendly explanations when I am stuck.

**Acceptance Criteria:**
- The student can type a programming-related question and receive a response from the AI.
- Responses are written in beginner-friendly language.
- The AI considers the student's current lesson or topic context when possible.
- Responses are relevant to programming concepts covered in the curriculum.
- The AI does not provide complete solutions to exercises — it explains concepts instead.

**Dependencies:**
- AUTH-01 (User Authentication)
- AUTH-02 (Role-Based Access — student role)
- External AI/LLM API integration
- Student context data (current lesson/topic)

---

### AI-02 — AI Error Explanation

**Priority:** Nice-to-Have

**User Story:**  
As a student, I want to submit a programming error or test error to the AI so that I can understand what went wrong and what I should learn next.

**Acceptance Criteria:**
- The student can paste or submit a programming error or test error message.
- The AI provides a clear and understandable explanation of the error.
- The AI suggests the relevant programming concept related to the error.
- The AI can recommend the next learning step or relevant lesson.
- Explanations are beginner-friendly and do not give away full solutions.

**Dependencies:**
- AUTH-01 (User Authentication)
- AUTH-02 (Role-Based Access — student role)
- External AI/LLM API integration
- Curriculum data (for learning step recommendations)
- GITHUB-02 (test error context, if integrated)
