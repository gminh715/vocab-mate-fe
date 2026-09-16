# Vocab Mate Web — Frontend

[![React](https://img.shields.io/badge/React-19.2%2B-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-8.1%2B-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-6.0%2B-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![MUI](https://img.shields.io/badge/MUI-v9.2%2B-007FFF?logo=mui&logoColor=white)](https://mui.com/)
[![TanStack Query](https://img.shields.io/badge/TanStack%20Query-v5.101%2B-FF4154?logo=reactquery&logoColor=white)](https://tanstack.com/query)
[![Tiptap](https://img.shields.io/badge/Tiptap-v3.28%2B-000000?logo=tiptap&logoColor=white)](https://tiptap.dev/)
[![Docker](https://img.shields.io/badge/Docker-Nginx%201.27-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Modern Single-Page Application (SPA) for **Vocab Mate** — an adaptive English reading and vocabulary acquisition platform featuring interactive CEFR word highlighting, in-context vocabulary lookup, and AI-powered spaced repetition exercises.

---

## Tech Stack

- **Framework & Build**: React 19.2, Vite 8.1, TypeScript ~6.0
- **UI & Styling**: Material UI (MUI v9.2), Emotion CSS-in-JS, custom responsive theme
- **Server State & Data Fetching**: TanStack React Query v5, Axios (with auto-refresh interceptor)
- **Forms & Validation**: React Hook Form, Zod v4, `@hookform/resolvers`
- **Routing & Guards**: React Router DOM v7 (Guest, Protected, Onboarding, Admin guards)
- **Rich Text Editor**: Tiptap v3 (`@tiptap/react`, starter kit, image, text align)
- **Internationalization**: `i18next` & `react-i18next` (English & Vietnamese)
- **Production Server**: Nginx 1.27 Alpine (SPA fallback routing + Gzip + API reverse proxy)

---

## Features

- **Distraction-Free Reader**: Read authentic articles with inline CEFR difficulty highlights (A1–C2) and reading streak tracking.
- **Contextual Word Drawer**: Instant definition, phonetics, and one-click saving of words to custom study collections.
- **AI Tutor Studio (FSRS-6.3)**: 4 adaptive exercise formats (Multiple Choice, Cloze, Sentence Construction, Definition Matching) with instant feedback.
- **Vocabulary Vault**: Organize, search, and review saved vocabulary by mastery level.
- **Admin CMS**: Rich-text article editor powered by Tiptap with image uploads and category management.

---

## Quickstart

### Prerequisites
- Node.js `>=22.0.0`
- npm `>=10.0.0`

### 1. Install Dependencies
```bash
npm ci
```

### 2. Configure Environment
```bash
cp .env.example .env
```

| Variable | Default | Description |
| :--- | :--- | :--- |
| `VITE_API_BASE_URL` | `/api/v1` | Relative API path for Axios client |
| `VITE_API_PROXY_TARGET` | `http://localhost:3000` | Backend URL forwarded by Vite dev server |

### 3. Start Development Server
```bash
npm run dev
```

App runs at: **[http://localhost:5173](http://localhost:5173)** (API requests to `/api/` are proxied to `:3000`).

---

## Docker Setup

### Standalone Container
```bash
docker build -t vocab-mate-frontend:latest .
docker run -d -p 5173:80 vocab-mate-frontend:latest
```

### Full-Stack with Docker Compose
```bash
docker compose up --build -d
```
Serves the frontend on port `5173` / `80` with Nginx handling SPA routing and reverse-proxying `/api/` to the backend container.

---

## Project Structure

```text
vocab-mate-frontend-python/
├── src/
│   ├── api/            # Axios client, interceptors & endpoint services
│   ├── components/     # UI components (Article, Tutor, Vocabulary, Layout, Shared)
│   ├── contexts/       # AuthContext, ThemeContext
│   ├── hooks/          # Custom hooks (useAuth, useTutor, etc.)
│   ├── i18n/           # Localization (en, vi)
│   ├── pages/          # Pages (Article, Tutor, Vault, Admin, Auth, Profile)
│   ├── routes/         # Route definitions & access guards
│   ├── theme.ts        # MUI custom theme tokens
│   ├── App.tsx         # Root app provider wrapper
│   └── main.tsx        # Vite client entrypoint
├── Dockerfile          # Multi-stage build (Node builder -> Nginx runner)
├── nginx.conf          # Nginx reverse proxy & SPA routing config
└── package.json        # Dependencies & scripts
```

---

## Available Scripts

```bash
npm run dev         # Start development server
npm run typecheck   # Type-check TypeScript without emit
npm run lint        # Scan codebase with ESLint
npm test            # Run Vitest test suite
npm run build       # Build production bundle in dist/
npm run preview     # Preview local production build
```

---

## License

[MIT License](LICENSE)
