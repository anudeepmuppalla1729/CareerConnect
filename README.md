# CareerConnect

Full-stack job & recruitment platform boilerplate (frontend + backend).

This repository contains two main folders:

- `backend/` - Express + MongoDB API server
- `frontend/` - React (Vite) single-page app

## Contents

- backend: API, models, controllers, routes, and utilities.
- frontend: React app (Vite) with components, pages, and API wrappers.

## Prerequisites

- Node.js (>= 18 recommended)
- npm (comes with Node.js)
- MongoDB URI (Atlas or local)

Optional services used by the backend:

- Cloudinary account (for uploads)
- Gmail account (or SMTP) for email sending

## Environment variables

Create a `.env` file in the `backend/` folder with at least the following variables:

- MONGO_URI=your_mongodb_connection_string
- JWT_SECRET_KEY=your_jwt_secret
- PORT=5000 (optional)
- CLOUDINARY_CLOUD_NAME=...
- CLOUDINARY_API_KEY=...
- CLOUDINARY_API_SECRET=...
- EMAIL_USER=your_email@gmail.com
- EMAIL_PASS=your_email_password_or_app_password

Notes:

- `EMAIL_USER` / `EMAIL_PASS` are used by the nodemailer transporter defined in `backend/config/emailTransporter.js`.
- The Cloudinary vars are referenced in `backend/config/cloudinary.js`.

## Backend - install & run

From the repository root:

1. Install dependencies

```powershell
cd backend; npm install
```

2. Run in development (auto-restarts with nodemon)

```powershell
npm run dev
```

3. Run production

```powershell
npm start
```

Useful backend scripts (defined in `backend/package.json`):

- `dev` — nodemon server.js (development)
- `start` — node server.js (production)

Seeding the database

The backend includes `seed.js` which populates the database with sample users, companies, jobs, articles and applications. To run it:

```powershell
# make sure MONGO_URI is set in backend/.env
cd backend; node seed.js
```

This script expects `MONGO_URI` to be present in the environment.

## Frontend - install & run

From the repository root:

1. Install dependencies

```powershell
cd frontend; npm install
```

2. Run development server

```powershell
npm run dev
```

3. Build for production

```powershell
npm run build
```

4. Preview production build locally

```powershell
npm run preview
```

Key frontend scripts (from `frontend/package.json`):

- `dev` — start Vite dev server
- `build` — produce production build
- `preview` — locally preview built app
- `lint` — run ESLint

By default the frontend expects an API available at `/api/*` paths. In development you may need to configure a proxy in Vite or set the API base URL used in `frontend/src/lib/axios.js`.

## Project notes

- Backend uses Express + Mongoose and exposes REST endpoints under `/api/*` (see `backend/routes/`).
- Frontend is built with React (Vite) and uses React Router + TanStack Query.
- Auth uses JWT signed with `JWT_SECRET_KEY` (see `backend/utils/jwt.js`).

## Troubleshooting

- If the backend cannot connect to MongoDB, verify `MONGO_URI` and network access (Atlas IP allowlist).
- For email sending with Gmail, use an App Password or enable "less secure apps" (not recommended).
- If uploads fail, verify Cloudinary credentials.

## Contributing

PRs and issues are welcome. Keep changes small and focused.

---

If you'd like, I can also:

- add a root-level npm script that bootstraps both frontend and backend concurrently;
- add a `.env.example` file listing required env variables;
- add a short developer script to run seed + dev servers.

Tell me which of these you'd like next and I will add them.
