# SportsPro — Sports Management System

Full-stack app for tournaments, teams, matches, and player stats. Roles: Super Admin, Coach, Player.

## Local setup (MongoDB Compass)

### 1. Start MongoDB and open Compass

Connect Compass to:

```
mongodb://127.0.0.1:27017
```

If Compass cannot connect, start **MongoDB Community** (Windows service `MongoDB`) first.

### 2. Create database `sportspro`

In Compass: **Create Database**

- Database name: `sportspro`
- Collection name: `_init` (optional; you can delete it later)

You can skip this step. The API creates `sportspro` on first connect.

### 3. Backend

```bash
cd backend
copy .env.example .env
npm install
npm run seed:admin
npm run dev
```

API: http://localhost:3001  
Health: http://localhost:3001/api/health

Default admin (change after login):

- Email: `admin@sportspro.com`
- Password: `Admin1234`

Refresh Compass → `sportspro` → `users`.

### 4. Frontend

```bash
cd frontend
copy .env.example .env
npm install
npm run dev
```

App: http://localhost:5173

Register as **Coach** or **Player**. Super admin is seed-only.

## Environment

| Variable | Where | Purpose |
|---|---|---|
| `MONGODB_URI` | backend | Default `mongodb://127.0.0.1:27017/sportspro` |
| `PORT` | backend | API port, **3001** |
| `JWT_SECRET` | backend | Required in production |
| `VITE_API_URL` | frontend | Must match backend, `http://localhost:3001` |

Do not commit `.env` files.

## Stack

- Frontend: React + Vite + Tailwind
- Backend: Express + JWT
- Database: MongoDB (Compass locally, or Atlas in production)

## Production

See `DEPLOYMENT_GUIDE.md`. Use a new Atlas database and new credentials — never reuse sample URIs from old docs.
