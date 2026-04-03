# Skill Match AI

[![Vercel](https://img.shields.io/badge/Vercel-Deployed-blue?logo=vercel)](https://skillmatchai-phi.vercel.app/)
[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)](https://nextjs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Database-green?logo=mongodb)](https://mongodb.com)
[![Firebase](https://img.shields.io/badge/Firebase-Auth%20%7C%20Realtime-orange?logo=firebase)](https://firebase.google.com)

An AI-powered hiring platform that connects recruiters with top talent through intelligent matching, skill gap analysis, and seamless interview management.

**Live Demo:** [https://skillmatchai-phi.vercel.app/](https://skillmatchai-phi.vercel.app/)

## Features

### For Candidates

- **AI-Powered Job Matching** - Find jobs that match your skills and experience
- **Skill Gap Analysis** - Identify missing skills and get personalized learning recommendations
- **Application Tracking** - Track your application status in real-time
- **Task Management** - Complete recruiter-assigned technical tasks
- **Interview Scheduling** - Easy scheduling with calendar integration
- **Profile Management** - Build a comprehensive professional profile

### For Recruiters

- **Smart Candidate Shortlisting** - AI-assisted candidate filtering and ranking
- **Pipeline Management** - Visual hiring pipeline with drag-and-drop stages
- **Task Assignment** - Send custom technical assessments to candidates
- **Interview Management** - Schedule and manage interviews effortlessly
- **Real-time Notifications** - Instant updates on candidate activities
- **Analytics Dashboard** - Track hiring metrics and performance

## Tech Stack

### Frontend

- **Next.js 14** - React framework with App Router
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide React** - Modern icon library
- **Firebase Authentication** - Secure user authentication
- **Recharts** - Data visualization for analytics

### Backend

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Firebase Admin SDK** - Server-side Firebase operations
- **Vercel Serverless Functions** - API deployment

### AI & Integrations

- **Gemini AI** - Content generation and analysis
- **Firebase Realtime Database** - Live updates
- **Vercel** - Frontend & backend hosting

## Project Structure

```
Skill/
├── Hireing-Platform-AI/           # Frontend Application
│   ├── src/
│   │   ├── app/                  # Next.js App Router
│   │   │   ├── (dashboard)/      # Dashboard routes
│   │   │   ├── api/              # API routes
│   │   │   ├── components/       # React components
│   │   │   └── lib/              # Utilities & hooks
│   │   └── public/               # Static assets
│   └── package.json
│
└── Hireing-Platform-AI-Server/    # Backend API
    ├── api/                      # Vercel serverless functions
    ├── routes/                   # API route handlers
    ├── config/                   # Database & Firebase config
    └── package.json
```

## Getting Started

### Prerequisites

- Node.js 18+
- MongoDB Atlas account
- Firebase project
- Vercel account

### Frontend Setup

1. Navigate to frontend directory:

```bash
cd Hireing-Platform-AI
```

2. Install dependencies:

```bash
npm install
```

3. Create `.env.local` file:

```env
NEXT_PUBLIC_API_BASE_URL=https://your-backend-url.vercel.app
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
NEXT_PUBLIC_FIREBASE_DATABASE_URL=https://your_project-default-rtdb.firebaseio.com
```

4. Run development server:

```bash
npm run dev
```

### Backend Setup

1. Navigate to backend directory:

```bash
cd Hireing-Platform-AI-Server
```

2. Install dependencies:

```bash
npm install
```

3. Create `.env` file:

```env
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/
FIREBASE_TYPE=service_account
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_PRIVATE_KEY_ID=your_private_key_id
FIREBASE_PRIVATE_KEY="your_private_key"
FIREBASE_CLIENT_EMAIL=your_client_email
FIREBASE_CLIENT_ID=your_client_id
FIREBASE_AUTH_URI=https://accounts.google.com/o/oauth2/auth
FIREBASE_TOKEN_URI=https://oauth2.googleapis.com/token
FIREBASE_AUTH_PROVIDER_CERT_URL=https://www.googleapis.com/oauth2/v1/certs
FIREBASE_CLIENT_CERT_URL=your_client_cert_url
```

4. Deploy to Vercel:

```bash
vercel --prod
```

## API Endpoints

### Authentication

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile/:uid` - Get user profile
- `PUT /api/auth/profile/:uid` - Update user profile

### Jobs

- `GET /api/jobs` - List all jobs
- `POST /api/jobs` - Create new job
- `GET /api/jobs/:id` - Get job details
- `PUT /api/jobs/:id` - Update job
- `DELETE /api/jobs/:id` - Delete job

### Applications

- `GET /api/applications/candidate/:uid` - Get candidate applications
- `GET /api/applications/recruiter/:uid` - Get recruiter applications
- `POST /api/jobs/:id/apply` - Apply to job
- `PUT /api/applications/:id/status` - Update application status

### Hiring Pipeline

- `GET /api/hiring-pipeline/:uid/summary` - Get pipeline summary
- `GET /api/hiring-pipeline/:uid/job/:jobId/summary` - Get job-specific summary

## Demo Accounts

### Candidate

- **Email:** `dipteskundu6@gmail.com`
- **Password:** `dipteskundu6@gmail.com`

### Recruiter

- **Email:** `diptesemon@gmail.com`
- **Password:** `diptesemon@gmail.com`

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.

## Support

For support, email support@skillmatchai.com or open an issue on GitHub.

## Acknowledgments

- Built with ❤️ by the Skill Match AI Team
- Powered by Next.js, MongoDB, and Firebase
- Deployed on Vercel

---

**Live Demo:** [https://skillmatchai.vercel.app](https://skillmatchai.vercel.app)

**Repository:** [https://github.com/Prosunsajal4/SkillMatchAI](https://github.com/Prosunsajal4/SkillMatchAI)
