# Job Portal

A full-stack job portal application built with React, Vite, Redux Toolkit, Node.js, Express, MongoDB, JWT authentication, and Cloudinary file uploads.

## Project Overview

This project provides a job application platform with two main user roles:

- **Student / Job Seeker**
  - Register and login with role-based access
  - Search and browse jobs
  - View job details
  - Apply for jobs
  - Update profile, upload resume, and manage skills

- **Recruiter / Admin**
  - Register companies and update company profiles
  - Post new jobs
  - See jobs created by the authenticated recruiter
  - View job applicants
  - Update application status

## Tech Stack

- Backend
  - Node.js
  - Express
  - MongoDB with Mongoose
  - JWT authentication
  - Cloudinary for file uploads
  - Multer + DataURI for image/resume uploads
  - Cookie-based authentication

- Frontend
  - React
  - Vite
  - React Router DOM
  - Redux Toolkit
  - Redux Persist
  - Tailwind CSS
  - Radix UI components
  - Axios
  - Framer Motion
  - Sonner notifications

## Repository Structure

```
backend/
  index.js
  controllers/
  middlewares/
  models/
  routes/
  utils/
frontend/
  src/
    components/
    hooks/
    redux/
    utils/
```

## Features

- Role-based registration and login (`student` or `recruiter`)
- Protected API routes for authenticated users
- Company registration and company profile updates
- Job posting and job search functionality
- Job application tracking and status updates
- Resume upload and profile photo upload via Cloudinary
- Admin dashboard routes for recruiters
- Client-side routing and state persistence using Redux Persist

## Getting Started

### Prerequisites

- Node.js 18+ installed
- npm or Yarn installed
- MongoDB connection string
- Cloudinary account credentials

### Backend Setup

1. Open a terminal and navigate to the backend folder:

```bash
cd backend
```

2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in `backend/` with the following variables:

```env
PORT=3000
MONGO_URI=your_mongodb_connection_string
SECRET_KEY=your_jwt_secret
CLOUD_NAME=your_cloudinary_cloud_name
API_KEY=your_cloudinary_api_key
API_SECRET=your_cloudinary_api_secret
```

4. Start the backend server:

```bash
npm run dev
```

The backend runs on `http://localhost:3000` by default.

### Frontend Setup

1. Open a separate terminal and navigate to the frontend folder:

```bash
cd frontend
```

2. Install dependencies:

```bash
npm install
```

3. Start the frontend development server:

```bash
npm run dev
```

The frontend runs on `http://localhost:5173` by default.

## API Endpoints

### User Routes

- `POST /api/v1/user/register`
- `POST /api/v1/user/login`
- `GET /api/v1/user/logout`
- `POST /api/v1/user/profile/update`

### Company Routes

- `POST /api/v1/company/register`
- `GET /api/v1/company/get`
- `GET /api/v1/company/get/:id`
- `PUT /api/v1/company/update/:id`

### Job Routes

- `POST /api/v1/job/post`
- `GET /api/v1/job/get`
- `GET /api/v1/job/getadminjobs`
- `GET /api/v1/job/get/:id`

### Application Routes

- `GET /api/v1/application/apply/:id`
- `GET /api/v1/application/get`
- `GET /api/v1/application/:id/applicants`
- `POST /api/v1/application/status/:id/update`

## Data Models

### User

- `fullname`
- `email`
- `phoneNumber`
- `password`
- `role` (`student` or `recruiter`)
- `profile` fields:
  - `bio`
  - `skills`
  - `resume`
  - `resumeOriginalName`
  - `company`
  - `profilePhoto`

### Company

- `name`
- `description`
- `website`
- `location`
- `logo`
- `userId`

### Job

- `title`
- `description`
- `requirements`
- `salary`
- `experienceLevel`
- `location`
- `jobType`
- `position`
- `company`
- `created_by`
- `applications`

### Application

- `job`
- `applicant`
- `status` (`pending`, `accepted`, `rejected`)

## Notes

- Backend authentication is cookie-based and protected via `isAuthenticated` middleware.
- Recruiter-specific app pages are guarded with a frontend `ProtectedRoute` wrapper.
- Cloudinary is used for image and resume uploads.

## Future Improvements

- Add dedicated environment setup examples or `.env.example`
- Add form validation and improved error handling
- Add unit tests for frontend and backend logic
- Add deployment scripts for production hosting

---

If you want, I can also add a `.env.example` template or extend the README with frontend-specific routes and usage examples.