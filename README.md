# Clever Learn - AI-Powered Study Platform

A full-stack Next.js application that harnesses the power of artificial intelligence to help improve students' critical thinking skills with AI, rather than replace those skills.

![Next.js](https://img.shields.io/badge/Next.js-13.4-black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.1-blue)
![Prisma](https://img.shields.io/badge/Prisma-6.19-2D3748)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.3-38B2AC)

🔗 **Live Demo**: [https://clever-learn-gilt.vercel.app/](https://clever-learn-gilt.vercel.app/)

## 🚀 Features

### AI Tutor Chatbots
- Interactive AI-powered tutors for personalized learning
- Context-aware conversations based on uploaded content
- Powered by Gemini AI for intelligent responses

### Content Processing
- **PDF Upload**: Upload PDF documents for AI analysis
- **Video Support**: Extract insights from video content
- **Audio Processing**: Transcribe and analyze audio files
- **Link Pasting**: Summarize content from URLs

### Quiz Generation
- AI-generated quizzes based on uploaded content
- Multiple choice questions with automatic grading
- Quiz attempt tracking and history
- Performance analytics

### Flashcard System
- Automatic flashcard generation from study materials
- Interactive flashcard review with flip animations
- Create and manage flashcard sets
- Add custom flashcards to existing sets

### User Management
- Google OAuth authentication
- User profile and settings management
- Generation limit tracking
- Personalized dashboard

## 🛠️ Tech Stack

- **Frontend**: Next.js 13, React 18, TypeScript, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL (Neon)
- **ORM**: Prisma
- **Auth**: NextAuth.js with Google OAuth
- **AI**: Google Gemini API
- **File Storage**: UploadThing
- **Realtime**: Supabase

## 📦 Installation

### Prerequisites
- Node.js 18+
- npm or yarn
- Neon account (for PostgreSQL)
- Google Cloud Console (for OAuth)
- UploadThing account (for file uploads)

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Pankaj-jangidd/clever-learn.git
   cd clever-learn
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   Create a `.env` file with:
   ```env
   # Auth
   GOOGLE_CLIENT_ID=your_google_client_id
   GOOGLE_CLIENT_SECRET=your_google_client_secret
   NEXTAUTH_SECRET=your_nextauth_secret
   
   # Database
   DATABASE_URL=your_postgresql_connection_string
   
   # AI
   GEMINI_API_KEY=your_gemini_api_key
   
   # Supabase
   NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
   
   # UploadThing
   UPLOADTHING_SECRET=your_uploadthing_secret
   UPLOADTHING_APP_ID=your_uploadthing_app_id
   
   # App Config
   NEXT_PUBLIC_URL=http://localhost:3000
   NEXT_PUBLIC_GENERATION_LIMIT=10
   GENERATION_LIMIT=25
   MAX_NUM=5
   ```

4. **Push database schema**
   ```bash
   npx prisma db push
   npx prisma generate
   ```

5. **Run the development server**
   ```bash
   npm run dev
   ```

6. **Open the application**
   ```
   http://localhost:3000
   ```

## 📁 Project Structure

```
├── app/
│   ├── api/
│   │   ├── auth/              # NextAuth endpoints
│   │   ├── chatgpt/           # AI chat endpoint
│   │   ├── flashcard-sets/    # Flashcard CRUD
│   │   ├── quizzes/           # Quiz management
│   │   ├── tutors/            # AI tutor endpoints
│   │   ├── uploadthing/       # File upload handler
│   │   └── user/              # User management
│   ├── (auth)/                # Auth pages (signin, signup)
│   ├── (dashboard)/           # Protected dashboard pages
│   │   ├── dashboard/         # Main dashboard
│   │   ├── flashcard-sets/    # Flashcard management
│   │   ├── quizzes/           # Quiz pages
│   │   ├── summarise/         # Content summarization
│   │   ├── settings/          # User settings
│   │   └── tutors/            # AI tutors
│   └── (marketing)/           # Landing page
├── components/                # Reusable UI components
├── lib/                       # Utility functions
├── prisma/                    # Database schema
└── public/                    # Static assets
```

## 🔌 API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET/POST | `/api/auth/[...nextauth]` | NextAuth.js handlers |

### Flashcard Sets
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/flashcard-sets` | List all flashcard sets |
| POST | `/api/flashcard-sets` | Create new flashcard set |
| GET | `/api/flashcard-sets/[id]` | Get single set |
| DELETE | `/api/flashcard-sets/[id]` | Delete flashcard set |
| POST | `/api/flashcard-sets/[id]/new-flashcard` | Add flashcard to set |

### Quizzes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/quizzes` | List all quizzes |
| POST | `/api/quizzes` | Create new quiz |
| GET | `/api/quizzes/[id]` | Get quiz details |
| DELETE | `/api/quizzes/[id]` | Delete quiz |
| POST | `/api/quizzes/[id]/attempts` | Submit quiz attempt |

### Tutors
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tutors` | List all tutors |
| POST | `/api/tutors` | Create new tutor |
| GET | `/api/tutors/[id]` | Get tutor details |
| POST | `/api/tutors/[id]/chat` | Chat with tutor |

### Utilities
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/file` | Process uploaded file |
| POST | `/api/link` | Process URL content |
| GET | `/api/limit` | Check generation limits |
| GET | `/api/user` | Get user profile |

## 🎨 Pages

| Route | Description |
|-------|-------------|
| `/` | Landing page |
| `/signin` | User sign in |
| `/signup` | User sign up |
| `/dashboard` | Main dashboard |
| `/flashcard-sets` | Flashcard sets list |
| `/flashcard-sets/new` | Create new flashcard set |
| `/flashcard-sets/[id]` | View/study flashcards |
| `/quizzes` | Quiz list |
| `/quizzes/new` | Create new quiz |
| `/quizzes/[id]` | View quiz details |
| `/quizzes/[id]/attempt` | Take quiz |
| `/tutors` | AI tutors list |
| `/tutors/new` | Create new tutor |
| `/tutors/[id]` | Chat with tutor |
| `/summarise` | Content summarization |
| `/settings` | User settings |

## 🔒 Security Features

- Google OAuth authentication via NextAuth.js
- Protected routes with session validation
- Environment variable protection for sensitive keys
- SQL injection protection via Prisma ORM
- Rate limiting on API endpoints
- Secure file upload handling

## 🚀 Deployment

This application is deployed on Vercel:

```bash
npm run build
```

Then deploy to Vercel:
```bash
vercel --prod
```

Don't forget to add all environment variables in your Vercel project settings.

## 📄 License

MIT License - feel free to use this project for learning purposes.

## 👤 Author

Built by [Pankaj Kumar](https://github.com/Pankaj-jangidd)
