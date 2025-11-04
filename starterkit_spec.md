---

# 🧱 **Clean Fullstack Starter Kit – Tech Specification**

## 🔰 Overview

Clean Fullstack Starter Kit adalah boilerplate modern berbasis **Next.js 15 (App Router)** dengan konfigurasi minimal namun siap pakai untuk pengembangan aplikasi fullstack TypeScript.
Tujuannya adalah menyediakan *foundation* yang bersih, modular, dan scalable tanpa kode contoh atau UI berlebih.

---

## ⚙️ Tech Stack

### Frontend / Fullstack Framework

* **Framework:** Next.js 15 (App Router)
* **Language:** TypeScript
* **Rendering:** Hybrid (SSR + ISR + CSR)
* **Bundler:** Turbopack
* **Routing:** App Router
* **State Management:** React Hooks (default)
  *Opsional: Zustand atau Jotai (belum di-install secara default)*

### UI & Styling

* **Tailwind CSS v4**
* **shadcn/ui**
* **Dark mode** via `next-themes`
* **Lucide React** untuk ikon

### Authentication

* **Better Auth** (tanpa preset user model)
* **Session management:** cookies + JWT fallback
* **Auth adapter:** siap diintegrasikan dengan Drizzle ORM
* **Default:** hanya endpoint `/api/auth/*` dan helper function di `lib/auth.ts`

### Database

* **ORM:** Drizzle ORM
* **Database:** PostgreSQL (Supabase / Neon / Railway)
* **Migration tools:** Drizzle Kit
* **Schema:** kosong (hanya file `schema.ts` kosong)
* **Connection:** via `DATABASE_URL` dari `.env`

### API & Backend

* **API Routes:** di folder `/app/api`
* **Data Fetching:** server actions + fetch server-side
* **Validation:** Zod (sudah terpasang)
* **Logging:** Consola (opsional)
* **Error Handling:** custom error wrapper (optional)

### Dev Environment

* **Linting:** ESLint + Prettier + TypeScript strict mode
* **Environment Management:** `.env.local` + `dotenv`
* **Commit Hooks:** Husky + Lint-Staged
* **Docker:** minimal `docker-compose.yml` (Postgres + web app)
* **CI/CD (opsional):** GitHub Actions (build & lint)

---

## 🧩 Folder Structure

```bash
src/
 ├── app/
 │   ├── layout.tsx
 │   ├── page.tsx
 │   └── api/
 │       └── health/route.ts  # default: return {status: 'ok'}
 │
 ├── components/
 │   └── ui/                  # tempat shadcn ui components
 │
 ├── lib/
 │   ├── db.ts                # drizzle db client
 │   ├── auth.ts              # better auth config
 │   ├── utils.ts             # helper function
 │   └── validation.ts        # Zod schemas
 │
 ├── db/
 │   ├── schema.ts
 │   └── drizzle.config.ts
 │
 ├── styles/
 │   └── globals.css
 │
 ├── hooks/
 │   └── use-theme.ts
 │
 ├── types/
 │   └── index.d.ts
 │
 └── config/
     └── site.ts              # metadata umum aplikasi
```

---

## 🔐 Environment Variables

```bash
# Development Environment Variables
# Copy this file to .env and modify as needed

# Database Configuration
DATABASE_URL=postgresql://postgres:postgres@localhost:5433/postgres
POSTGRES_DB=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres

# Authentication
BETTER_AUTH_SECRET=your_secret_key_here
BETTER_AUTH_URL=http://localhost:3000
NEXT_PUBLIC_BETTER_AUTH_URL=http://localhost:3000
```

---

## 🧰 Setup Commands

```bash
# Install dependencies
pnpm install

# Setup database
pnpm drizzle-kit generate && pnpm drizzle-kit push

# Dev server
pnpm dev

# Lint & format
pnpm lint && pnpm format
```

---

## 🚀 Features Checklist

| Fitur                            | Status | Catatan                |
| -------------------------------- | :----: | ---------------------- |
| Next.js 15 (App Router)          |    ✅   | Sudah dikonfigurasi    |
| TypeScript strict mode           |    ✅   | Aktif                  |
| Tailwind + shadcn/ui base        |    ✅   | Kosong, siap pakai     |
| Better Auth                      |    ✅   | Config dasar saja      |
| Drizzle ORM + PostgreSQL         |    ✅   | File schema kosong     |
| Dark mode system                 |    ✅   | Sudah terset           |
| Dockerfile + docker-compose      |    ✅   | Untuk dev setup        |
| Health check route `/api/health` |    ✅   | Return `{status:"ok"}` |
| Zod Validation ready             |    ✅   | Global import          |
| ESLint + Prettier + Husky        |    ✅   | Untuk konsistensi kode |

---

