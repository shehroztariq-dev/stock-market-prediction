# MediaShare

A simple media sharing app with a FastAPI backend and a React frontend. Users can upload, view, and share photos and videos.

## Features

- Upload images and videos
- Browse a feed of shared media
- User authentication (sign up / log in)
- Like and comment on posts
- Delete your own uploads

## Tech Stack

**Backend**

- FastAPI (Python)
- SQLAlchemy + PostgreSQL (or SQLite for local dev)
- Uvicorn (ASGI server)
- JWT-based authentication

**Frontend**

- React
- Axios for API calls
- React Router

## Project Structure

```
.
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── models.py
│   │   ├── routes/
│   │   └── database.py
│   ├── requirements.txt
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.jsx
│   ├── package.json
│   └── .env.example
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.10+
- Node.js 18+
- PostgreSQL (optional, SQLite works for local dev)

### Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env       # update with your own settings
uvicorn app.main:app --reload
```

The API will be running at `http://localhost:8000`.
Interactive docs are available at `http://localhost:8000/docs`.

### Frontend Setup

```bash
cd frontend
npm install
cp .env.example .env       # set VITE_API_URL or similar
npm run dev
```

The app will be running at `http://localhost:5173` (or your configured port).

## Environment Variables

**Backend (`.env`)**

```
DATABASE_URL=postgresql://user:password@localhost/mediashare
SECRET_KEY=your-secret-key
UPLOAD_DIR=./uploads
```

**Frontend (`.env`)**

```
VITE_API_URL=http://localhost:8000
```

## API Overview

| Method | Endpoint         | Description            |
| ------ | ---------------- | ---------------------- |
| POST   | /auth/register   | Create a new account   |
| POST   | /auth/login      | Log in and get a token |
| GET    | /media           | List shared media      |
| POST   | /media           | Upload new media       |
| DELETE | /media/{id}      | Delete your own media  |
| POST   | /media/{id}/like | Like a post            |

## Running Tests

```bash
cd backend
pytest
```

## License

MIT
