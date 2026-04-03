# Skill Match AI - Complete Technical Documentation

## Table of Contents
1. [Project Overview](#project-overview)
2. [Technology Stack](#technology-stack)
3. [Architecture Overview](#architecture-overview)
4. [Frontend Libraries & Dependencies](#frontend-libraries--dependencies)
5. [Backend Libraries & Dependencies](#backend-libraries--dependencies)
6. [Database Schema](#database-schema)
7. [User Roles & Flows](#user-roles--flows)
8. [Page-by-Page Documentation](#page-by-page-documentation)
9. [API Endpoints](#api-endpoints)
10. [Authentication & Security](#authentication--security)
11. [Real-time Features](#real-time-features)
12. [AI Integration](#ai-integration)
13. [Deployment Configuration](#deployment-configuration)

---

## Project Overview

**Skill Match AI** is a comprehensive AI-powered hiring platform that streamlines the recruitment process through intelligent candidate-job matching, skill gap analysis, and automated interview management.

**Live URL:** https://skillmatchai-phi.vercel.app/
**Repository:** https://github.com/Prosunsajal4/SkillMatchAI

### Core Features
- AI-driven job-candidate matching
- Real-time application tracking
- Skill gap detection and analysis
- Automated interview scheduling
- Task assignment and submission system
- Communication verification scoring
- Multi-role dashboard (Admin, Recruiter, Candidate)

---

## Technology Stack

### Frontend
| Technology | Version | Purpose |
|------------|---------|---------|
| Next.js | 14.x | React framework with App Router |
| React | 18.x | UI library |
| Tailwind CSS | 3.x | Utility-first styling |
| Firebase Auth | 10.x | Authentication |
| Firebase Realtime DB | 10.x | Real-time updates |
| Recharts | 2.x | Data visualization |
| Lucide React | 0.x | Icons |
| date-fns | 3.x | Date formatting |
| html-to-image | 1.x | Screenshot generation |
| next-themes | 0.x | Dark/light mode |

### Backend
| Technology | Version | Purpose |
|------------|---------|---------|
| Node.js | 18+ | Runtime environment |
| Express.js | 4.x | Web framework |
| MongoDB | 6.x | Primary database |
| Mongoose | 8.x | MongoDB ODM |
| Firebase Admin | 12.x | Server-side Firebase |
| Multer | 1.x | File uploads |
| CORS | 2.x | Cross-origin requests |
| dotenv | 16.x | Environment variables |

### AI & External Services
| Service | Purpose |
|---------|---------|
| Gemini AI | Content generation, skill analysis |
| Firebase RTDB | Real-time notifications |
| MongoDB Atlas | Cloud database hosting |
| Vercel | Frontend & API hosting |

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                        CLIENT LAYER                          │
│  ┌──────────────────┐  ┌──────────────────┐                 │
│  │   Next.js App    │  │  Candidate View  │                 │
│  │   (Frontend)     │  │  Recruiter View  │                 │
│  └────────┬─────────┘  └────────┬─────────┘                 │
└───────────┼────────────────────┼────────────────────────────┘
            │                    │
            ▼                    ▼
┌─────────────────────────────────────────────────────────────┐
│                      API GATEWAY (Vercel)                    │
│  ┌──────────────────────────────────────────────────────┐   │
│  │              Express.js Serverless Functions          │   │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │   │
│  │  │  Auth    │ │  Jobs    │ │  Apps    │ │ Tasks  │ │   │
│  │  │  Routes  │ │  Routes  │ │  Routes  │ │ Routes │ │   │
│  │  └──────────┘ └──────────┘ └──────────┘ └────────┘ │   │
│  └──────────────────────────────────────────────────────┘   │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                      DATA LAYER                              │
│  ┌──────────────────┐  ┌──────────────────┐                │
│  │   MongoDB Atlas  │  │ Firebase RTDB    │                │
│  │   (Primary DB)   │  │ (Real-time)      │                │
│  └──────────────────┘  └──────────────────┘                │
└─────────────────────────────────────────────────────────────┘
```

---

## Frontend Libraries & Dependencies

### Core Framework
```json
{
  "next": "^14.2.0",
  "react": "^18.3.0",
  "react-dom": "^18.3.0"
}
```

### Styling & UI
```json
{
  "tailwindcss": "^3.4.0",
  "lucide-react": "^0.400.0",
  "class-variance-authority": "^0.7.0",
  "clsx": "^2.1.0",
  "tailwind-merge": "^2.3.0"
}
```

### Firebase Integration
```json
{
  "firebase": "^10.12.0",
  "@firebase/auth": "^1.7.0",
  "@firebase/database": "^1.0.0"
}
```

### Data Visualization
```json
{
  "recharts": "^2.12.0",
  "html-to-image": "^1.11.0"
}
```

### Utilities
```json
{
  "date-fns": "^3.6.0",
  "next-themes": "^0.3.0",
  "@radix-ui/react-dialog": "^1.0.0",
  "@radix-ui/react-dropdown-menu": "^2.0.0",
  "@radix-ui/react-slot": "^1.0.0"
}
```

---

## Backend Libraries & Dependencies

### Server Framework
```json
{
  "express": "^4.19.0",
  "cors": "^2.8.5",
  "dotenv": "^16.4.0"
}
```

### Database
```json
{
  "mongodb": "^6.5.0",
  "mongoose": "^8.3.0"
}
```

### Firebase Admin
```json
{
  "firebase-admin": "^12.1.0"
}
```

### File Handling
```json
{
  "multer": "^1.4.5-lts.1",
  "formidable": "^3.5.0"
}
```

### AI Integration
```json
{
  "@google/generative-ai": "^0.21.0"
}
```

---

## Database Schema

### Collections

#### 1. Users Collection
```javascript
{
  _id: ObjectId,
  firebaseUid: String,        // Firebase authentication ID
  email: String,
  displayName: String,
  role: String,               // 'candidate', 'recruiter', 'admin'
  
  // For candidates
  skills: [String],
  experience: [{
    title: String,
    company: String,
    duration: String,
    description: String
  }],
  education: [{
    degree: String,
    institution: String,
    year: String
  }],
  
  // For recruiters
  companyName: String,
  companyDescription: String,
  
  // Common
  photoURL: String,
  phone: String,
  location: String,
  bio: String,
  createdAt: Date,
  updatedAt: Date
}
```

#### 2. Jobs Collection (find_jobs)
```javascript
{
  _id: ObjectId,
  title: String,
  company: String,
  location: String,
  salary: String,
  salaryRange: String,
  experienceLevel: String,
  employmentType: String,     // Full-time, Part-time, Contract, Internship
  workMode: String,          // Remote, On-site, Hybrid
  category: String,
  description: String,
  responsibilities: String,
  skills: [String],
  vacancy: Number,
  deadline: Date,
  postedBy: String,          // Recruiter's firebaseUid
  posted: String,            // Date string
  status: String,            // 'active', 'closed', 'draft'
  createdAt: Date
}
```

#### 3. Applications Collection
```javascript
{
  _id: ObjectId,
  jobId: ObjectId,
  firebaseUid: String,       // Candidate's ID
  email: String,
  jobTitle: String,
  company: String,
  location: String,
  status: String,           // 'submitted', 'seen', 'shortlisted', 
                            // 'task_sent', 'task_submitted', 
                            // 'interview_selected', 'interviewing', 
                            // 'hired', 'rejected'
  aiScore: Number,
  matchPercentage: Number,
  timeline: [{
    status: String,
    timestamp: Date
  }],
  feedback: String,
  communicationScore: Number,
  communicationStatus: String,
  candidateName: String,
  candidatePhoto: String,
  skills: [String],
  createdAt: Date,
  updatedAt: Date
}
```

#### 4. Tasks Collection
```javascript
{
  _id: ObjectId,
  jobId: ObjectId,
  recruiterId: String,
  applicationId: ObjectId,
  applicantId: String,
  
  // Task Details
  title: String,
  description: String,
  instructions: String,
  deadline: Date,
  status: String,           // 'pending', 'accepted', 'submitted', 'reviewed'
  
  // Submissions
  submission: {
    content: String,
    attachments: [String],
    submittedAt: Date,
    feedback: String,
    score: Number
  },
  
  createdAt: Date,
  updatedAt: Date
}
```

#### 5. Interviews Collection
```javascript
{
  _id: ObjectId,
  jobId: ObjectId,
  applicationId: ObjectId,
  recruiterId: String,
  applicantId: String,
  
  // Interview Details
  type: String,            // 'video', 'phone', 'in-person'
  date: String,
  time: String,
  duration: String,
  meetingLink: String,
  location: String,
  
  // Status
  status: String,         // 'scheduled', 'completed', 'cancelled'
  notes: String,
  feedback: String,
  
  createdAt: Date,
  updatedAt: Date
}
```

#### 6. Notifications Collection
```javascript
{
  _id: ObjectId,
  userId: String,          // Recipient's firebaseUid
  type: String,           // 'status_update', 'task_assigned', 
                          // 'interview_scheduled', 'job_posted'
  title: String,
  message: String,
  
  // Related IDs
  jobId: ObjectId,
  applicationId: ObjectId,
  taskId: ObjectId,
  
  isRead: Boolean,
  createdAt: Date
}
```

#### 7. Saved Jobs Collection
```javascript
{
  _id: ObjectId,
  firebaseUid: String,    // Candidate's ID
  jobId: ObjectId,
  createdAt: Date
}
```

---

## User Roles & Flows

### 1. Candidate Flow

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Sign Up    │───▶│ Build Profile│───▶│  Browse Jobs │
└──────────────┘    └──────────────┘    └──────────────┘
                                               │
                                               ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  Get Hired   │◀───│  Interview   │◀───│   Apply      │
└──────────────┘    └──────────────┘    └──────────────┘
     ▲                                            │
     │                                            ▼
     │                                    ┌──────────────┐
     │                                    │ Skill Gap    │
     │                                    │ Analysis     │
     │                                    └──────────────┘
     │
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  Complete    │◀───│   Submit     │◀───│   Receive    │
│   Task       │    │    Task      │    │    Task      │
└──────────────┘    └──────────────┘    └──────────────┘
```

**Candidate Pages:**
- `/signin` - Login page
- `/signup` - Registration
- `/jobs` - Browse all jobs
- `/jobs/[id]` - Job details
- `/applications` - My applications
- `/my-tasks` - Assigned tasks
- `/profile` - View profile
- `/profile/edit` - Edit profile
- `/saved-jobs` - Saved/bookmarked jobs
- `/skill-gap-detection` - AI skill analysis
- `/communication-verification` - Communication test
- `/interviews` - Scheduled interviews

### 2. Recruiter Flow

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Sign Up    │───▶│   Post Job   │───▶│   Review     │
│  (Recruiter) │    │              │    │ Applications│
└──────────────┘    └──────────────┘    └──────────────┘
                                               │
                                               ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Hire       │◀───│   Interview  │◀───│  Shortlist   │
│ Candidate    │    │  Candidate   │    │  Candidates  │
└──────────────┘    └──────────────┘    └──────────────┘
     ▲                                            │
     │                                            ▼
     │                                    ┌──────────────┐
     │                                    │ Assign Task  │
     │                                    │              │
     │                                    └──────────────┘
```

**Recruiter Pages:**
- `/dashboard` - Recruiter overview with analytics
- `/my-jobs` - Manage posted jobs
- `/applicants` - All applicants for recruiter's jobs
- `/shortlisted` - Shortlisted candidates
- `/task-assignment` - Assign tasks to candidates
- `/interviews` - Manage interviews
- `/profile` - Recruiter profile

### 3. Admin Flow

**Admin Pages:**
- `/admin/dashboard` - Platform analytics
- `/admin/users` - User management
- `/admin/jobs` - All jobs management
- `/admin/reports` - System reports

---

## Page-by-Page Documentation

### PUBLIC PAGES

#### 1. Landing Page (`/`)
**Purpose:** Marketing page showcasing platform features
**Components:**
- Hero section with CTA
- Feature highlights
- How it works section
- Testimonials
- Footer

**Libraries Used:**
- Lucide React for icons
- Next.js Image optimization
- Tailwind CSS animations

---

#### 2. Sign In (`/signin`)
**Purpose:** User authentication
**Features:**
- Email/password login
- Quick access demo accounts
- Password visibility toggle
- Error handling

**Libraries:**
- Firebase Authentication
- React Hook Form (implied)
- Lucide React icons

**Demo Accounts:**
- Candidate: dipteskundu6@gmail.com / dipteskundu6@gmail.com
- Recruiter: diptesemon@gmail.com / diptesemon@gmail.com

---

#### 3. Sign Up (`/signup`)
**Purpose:** User registration
**Features:**
- Role selection (Candidate/Recruiter)
- Email verification
- Profile setup wizard
- Terms acceptance

---

### CANDIDATE PAGES

#### 4. Jobs Page (`/jobs`)
**Purpose:** Browse and search available jobs
**Features:**
- Advanced filtering (category, location, type)
- Search functionality
- Pagination
- Job cards with match percentage
- Save/bookmark jobs
- Apply modal

**API Calls:**
- `GET /api/jobs` - Fetch all jobs
- `POST /api/jobs/:id/apply` - Apply to job
- `POST /api/saved-jobs` - Save job

**Components:**
- JobCard
- FilterSidebar
- SearchBar
- ApplyModal
- Pagination

---

#### 5. Job Detail (`/jobs/[id]`)
**Purpose:** View complete job information
**Features:**
- Full job description
- Company details
- Requirements list
- Skills match visualization
- Apply button
- Similar jobs

**API Calls:**
- `GET /api/jobs/:id` - Job details
- `GET /api/jobs/:id/related` - Similar jobs

---

#### 6. My Applications (`/applications`)
**Purpose:** Track application status
**Features:**
- Application cards with status
- Timeline visualization
- Status filter
- Withdraw application
- View job details

**API Calls:**
- `GET /api/applications/candidate/:uid` - User applications
- `PUT /api/applications/:id/withdraw` - Withdraw

**Status Flow:**
```
submitted → seen → shortlisted → task_sent → 
task_submitted → interview_selected → interviewing → hired
```

---

#### 7. My Tasks (`/my-tasks`)
**Purpose:** Complete recruiter-assigned tasks
**Features:**
- Task list with deadlines
- Task detail view
- Submission form
- File upload
- Feedback viewing

**API Calls:**
- `GET /api/tasks/candidate/:uid` - Get tasks
- `POST /api/tasks/:id/submit` - Submit task
- `PUT /api/tasks/:id/accept` - Accept task

---

#### 8. Skill Gap Analysis (`/skill-gap-detection`)
**Purpose:** AI-powered skill improvement recommendations
**Features:**
- Upload resume
- Compare with job requirements
- Missing skills identification
- Learning resources
- Progress tracking

**Libraries:**
- Gemini AI API
- PDF parsing
- html-to-image

---

#### 9. Profile (`/profile` & `/profile/edit`)
**Purpose:** Manage candidate profile
**Features:**
- Personal information
- Skills management
- Experience & education
- Portfolio links
- Resume upload
- Profile completion percentage

---

### RECRUITER PAGES

#### 10. Recruiter Dashboard (`/dashboard`)
**Purpose:** Overview of recruitment activities
**Features:**
- Hiring pipeline visualization
- Metrics cards (Active Jobs, Applicants, Shortlisted, Interviews)
- Recent applications
- Quick job posting
- Performance charts

**Libraries:**
- Recharts for charts
- Firebase Realtime Database for live counts

**API Calls:**
- `GET /api/dashboard/recruiter/:uid` - Dashboard data
- `GET /api/hiring-pipeline/:uid/summary` - Pipeline stats

---

#### 11. My Jobs (`/my-jobs`)
**Purpose:** Manage posted jobs
**Features:**
- Job list with applicant counts
- Edit/close jobs
- View applicants per job
- Duplicate job
- Job statistics

**API Calls:**
- `GET /api/jobs/recruiter/:uid` - Recruiter jobs
- `PUT /api/jobs/:id` - Update job
- `DELETE /api/jobs/:id` - Delete job

---

#### 12. All Applicants (`/applicants`)
**Purpose:** View all job applicants
**Features:**
- Applicant cards
- Status filtering
- Shortlist action
- Reject action
- View profile
- Send message

**API Calls:**
- `GET /api/applications/recruiter/:uid` - All applications
- `PUT /api/applications/:id/status` - Update status

---

#### 13. Shortlisted (`/shortlisted`)
**Purpose:** Manage shortlisted candidates
**Features:**
- Shortlisted candidate cards
- Assign tasks
- Schedule interviews
- Remove from shortlist
- Bulk actions

**API Calls:**
- `GET /api/applications/recruiter/:uid/status/shortlisted` - Shortlisted
- `POST /api/tasks` - Create task
- `POST /api/interviews` - Schedule interview

---

#### 14. Task Assignment (`/task-assignment`)
**Purpose:** Create and assign tasks
**Features:**
- Task creation form
- Candidate selection
- Deadline setting
- Instructions editor
- Template selection

**API Calls:**
- `POST /api/tasks` - Create task
- `GET /api/applications/recruiter/:uid/status/shortlisted` - Get candidates

---

#### 15. Interviews (`/interviews`)
**Purpose:** Interview management
**Features:**
- Interview calendar
- Schedule new interview
- Video meeting links
- Interview notes
- Reschedule/cancel

**API Calls:**
- `GET /api/interviews/recruiter/:uid` - Recruiter interviews
- `POST /api/interviews` - Create interview
- `PUT /api/interviews/:id` - Update interview

---

### ADMIN PAGES

#### 16. Admin Dashboard (`/admin/dashboard`)
**Purpose:** Platform-wide analytics
**Features:**
- User statistics
- Job statistics
- Application metrics
- Revenue tracking (if applicable)
- System health

---

#### 17. User Management (`/admin/users`)
**Purpose:** Manage platform users
**Features:**
- User list
- Role management
- Account activation/deactivation
- View user details
- Bulk actions

---

## API Endpoints

### Authentication Routes
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | User login |
| GET | `/api/auth/profile/:uid` | Get user profile |
| PUT | `/api/auth/profile/:uid` | Update profile |
| PUT | `/api/auth/change-password` | Change password |

### Job Routes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/jobs` | List all jobs |
| GET | `/api/jobs/:id` | Get job details |
| POST | `/api/jobs` | Create job (recruiter) |
| PUT | `/api/jobs/:id` | Update job |
| DELETE | `/api/jobs/:id` | Delete job |
| GET | `/api/jobs/recruiter/:uid` | Get recruiter's jobs |
| POST | `/api/jobs/:id/apply` | Apply to job |

### Application Routes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/applications/candidate/:uid` | Candidate applications |
| GET | `/api/applications/recruiter/:uid` | Recruiter applications |
| GET | `/api/applications/recruiter/:uid/status/:status` | Filtered applications |
| PUT | `/api/applications/:id/status` | Update status |
| PUT | `/api/applications/:id/withdraw` | Withdraw application |

### Task Routes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks/candidate/:uid` | Candidate tasks |
| GET | `/api/tasks/recruiter/:uid` | Recruiter tasks |
| POST | `/api/tasks` | Create task |
| PUT | `/api/tasks/:id/submit` | Submit task |
| PUT | `/api/tasks/:id/accept` | Accept task |

### Interview Routes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/interviews/candidate/:uid` | Candidate interviews |
| GET | `/api/interviews/recruiter/:uid` | Recruiter interviews |
| POST | `/api/interviews` | Schedule interview |
| PUT | `/api/interviews/:id` | Update interview |
| DELETE | `/api/interviews/:id` | Cancel interview |

### Hiring Pipeline Routes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/hiring-pipeline/:uid/summary` | Pipeline summary |
| GET | `/api/hiring-pipeline/:uid/job/:jobId/summary` | Job pipeline |

---

## Authentication & Security

### Firebase Authentication
- Email/password authentication
- Email verification required for recruiters
- Token-based session management
- Automatic token refresh

### Security Measures
- Environment variables for sensitive data
- MongoDB connection string protection
- Firebase service account key security
- CORS configuration
- Input validation on all routes
- XSS protection through React escaping

### Role-Based Access Control (RBAC)
- Middleware checks user role
- Route-level permission validation
- API endpoint authorization
- UI component conditional rendering

---

## Real-time Features

### Firebase Realtime Database Structure
```
jobmatching-c7f31-default-rtdb/
├── jobApplicants/
│   └── {jobId}/
│       ├── count: number
│       └── lastUpdated: timestamp
├── notifications/
│   └── {userId}/
│       └── {notificationId}/
│           ├── type: string
│           ├── message: string
│           ├── timestamp: number
│           └── isRead: boolean
└── userPresence/
    └── {userId}/
        ├── online: boolean
        └── lastSeen: timestamp
```

### Real-time Hooks
- `useRecruiterPipelineRealtime` - Live pipeline updates
- `useRealtimeNotifications` - Instant notifications
- `useApplicantCounts` - Live applicant counters

---

## AI Integration

### Gemini AI Usage
1. **Skill Gap Analysis**
   - Input: Candidate skills + Job requirements
   - Output: Missing skills + Learning recommendations

2. **Communication Scoring**
   - Input: Communication test responses
   - Output: Score + Feedback

3. **Job Description Enhancement**
   - Input: Basic job details
   - Output: Optimized description

### AI Score Calculation
```javascript
// Match percentage calculation
const calculateMatch = (candidateSkills, jobSkills) => {
  const matching = candidateSkills.filter(skill => 
    jobSkills.includes(skill.toLowerCase())
  );
  return (matching.length / jobSkills.length) * 100;
};
```

---

## Deployment Configuration

### Vercel Configuration (vercel.json)
```json
{
  "version": 2,
  "builds": [
    {
      "src": "api/index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/api/(.*)",
      "dest": "api/index.js"
    }
  ],
  "env": {
    "MONGO_URI": "@mongo-uri",
    "FIREBASE_PROJECT_ID": "@firebase-project-id"
  }
}
```

### Environment Variables

#### Frontend (.env.local)
```
NEXT_PUBLIC_API_BASE_URL=https://skillmatchaiserver.vercel.app
NEXT_PUBLIC_FIREBASE_API_KEY=
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=
NEXT_PUBLIC_FIREBASE_PROJECT_ID=
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=
NEXT_PUBLIC_FIREBASE_APP_ID=
NEXT_PUBLIC_FIREBASE_DATABASE_URL=
```

#### Backend (.env)
```
MONGO_URI=
FIREBASE_TYPE=service_account
FIREBASE_PROJECT_ID=
FIREBASE_PRIVATE_KEY_ID=
FIREBASE_PRIVATE_KEY=
FIREBASE_CLIENT_EMAIL=
FIREBASE_CLIENT_ID=
FIREBASE_AUTH_URI=
FIREBASE_TOKEN_URI=
FIREBASE_AUTH_PROVIDER_CERT_URL=
FIREBASE_CLIENT_CERT_URL=
GEMINI_API_KEY=
```

---

## File Structure

```
Skill/
├── Hireing-Platform-AI/              # Frontend
│   ├── src/
│   │   ├── app/
│   │   │   ├── (dashboard)/         # Dashboard routes
│   │   │   │   ├── applicants/
│   │   │   │   ├── interviews/
│   │   │   │   ├── my-jobs/
│   │   │   │   ├── my-tasks/
│   │   │   │   ├── profile/
│   │   │   │   ├── shortlisted/
│   │   │   │   └── task-assignment/
│   │   │   ├── admin/               # Admin routes
│   │   │   ├── api/                 # API routes
│   │   │   ├── components/          # React components
│   │   │   │   ├── calendar/
│   │   │   │   ├── common/
│   │   │   │   ├── form/
│   │   │   │   ├── modals/
│   │   │   │   ├── notifications/
│   │   │   │   └── recruiter/
│   │   │   ├── dashboard/           # Dashboard components
│   │   │   ├── jobs/                # Job-related pages
│   │   │   ├── lib/                 # Utilities
│   │   │   │   ├── apiClient.js
│   │   │   │   ├── firebaseClient.js
│   │   │   │   ├── realtimeHooks.js
│   │   │   │   └── uiRefresh.js
│   │   │   └── globals.css
│   │   └── public/
│   ├── package.json
│   └── next.config.js
│
├── Hireing-Platform-AI-Server/      # Backend
│   ├── api/
│   │   └── index.js                 # Main entry
│   ├── routes/
│   │   ├── applications.routes.js
│   │   ├── auth.routes.js
│   │   ├── chatbot.routes.js
│   │   ├── dashboard.routes.js
│   │   ├── hiring-pipeline.routes.js
│   │   ├── interviews.routes.js
│   │   ├── jobs.routes.js
│   │   ├── notifications.routes.js
│   │   ├── tasks.routes.js
│   │   └── transparency.routes.js
│   ├── config/
│   │   ├── db.js
│   │   └── firebaseAdmin.js
│   ├── middleware/
│   │   └── auth.js
│   ├── package.json
│   └── vercel.json
│
└── README.md
```

---

## Summary

**Skill Match AI** is a comprehensive hiring platform built with modern web technologies:

- **Frontend:** Next.js 14 + React + Tailwind CSS + Firebase
- **Backend:** Node.js + Express + MongoDB + Firebase Admin
- **AI:** Gemini AI for skill analysis and content generation
- **Real-time:** Firebase Realtime Database for live updates
- **Hosting:** Vercel for both frontend and backend

The platform serves three user types with distinct workflows:
1. **Candidates** - Find jobs, apply, track applications, complete tasks
2. **Recruiters** - Post jobs, review applicants, manage hiring pipeline
3. **Admins** - Platform management and analytics

All features are designed to streamline the hiring process through intelligent automation and real-time collaboration.

---

**Document Version:** 1.0  
**Last Updated:** April 2026  
**Author:** Skill Match AI Team
