# Project README

This repository contains a Rust backend and a Vite+React frontend. These instructions let anyone clone the repo and run both parts locally for development.

**Prerequisites**
- Git
- Rust (rustc & cargo)
- Node.js (LTS) and pnpm (or npm/yarn)
- Docker & Docker Compose (for local Postgres)

**Clone the repository**

```bash
git clone <your-repo-url> my-project
cd my-project
```

**Start the backend database**

From the repo root, start the development database defined in the backend folder:

```bash
cd backend
docker compose up -d
```

Apply the schema if needed (optional):

```bash
# using psql from the host or from the running container
psql -h localhost -U user -d postgres-db -f migrations.sql
```

**Run the backend**

In another terminal (from repo root):

```bash
cd backend
cargo run
```

The backend README has more details: [backend/readme.md](backend/readme.md).

**Run the frontend**

In a separate terminal (from repo root):

```bash
cd frontend
pnpm install
pnpm run dev
```

Open the frontend URL shown by Vite (usually http://localhost:5173). The frontend README has additional info: [frontend/README.md](frontend/README.md).

**Build for production**

Backend (release build):

```bash
cd backend
cargo build --release
```

Frontend (static bundle):

```bash
cd frontend
pnpm run build
pnpm run preview
```

**Troubleshooting & notes**
- If ports conflict, change configuration in the backend files and the Vite config.
- On Windows, run commands in Git Bash, WSL, or PowerShell (adjust `psql` invocation accordingly).
- For authentication setup see [backend/AUTH_SETUP.md](backend/AUTH_SETUP.md).

If you want, I can also add a single-script `dev.sh`/`dev.ps1` or a root `docker-compose.yml` to run everything together — would you like that?
