# 🧱 Clean Fullstack Starter Kit

A modern, clean fullstack starter kit built with **Next.js 15 (App Router)**, TypeScript, and a minimal yet powerful tech stack.

## ✨ Features

- ⚡ **Next.js 15** with App Router and Turbopack
- 🎨 **Tailwind CSS** + **shadcn/ui** components
- 🔐 **Better Auth** for authentication
- 🗄️ **Drizzle ORM** + **PostgreSQL**
- 🌙 **Dark mode** support via `next-themes`
- ✅ **TypeScript** strict mode
- 📦 **Zod** for validation
- 🛠️ **ESLint** + **Prettier** + **Husky** for code quality
- 🐳 **Docker** setup for development

## 🚀 Quick Start

### Prerequisites

- Node.js 20+ 
- npm, pnpm, or yarn (npm works perfectly!)
- PostgreSQL (or use Docker)

### Installation

1. **Install dependencies**

   Using npm:
   ```bash
   npm install
   ```

   Or using pnpm:
   ```bash
   pnpm install
   ```

   Or using yarn:
   ```bash
   yarn install
   ```

2. **Setup environment variables**

   ```bash
   # On Windows (PowerShell)
   copy .env.example .env.local
   
   # On macOS/Linux
   cp .env.example .env.local
   ```

   Edit `.env.local` with your configuration:
   - `DATABASE_URL` - Your PostgreSQL connection string
   - `BETTER_AUTH_SECRET` - Generate a secure secret key
   - `BETTER_AUTH_URL` - Your app URL (default: http://localhost:3000)

3. **Setup database**

   Using npm:
   ```bash
   # Generate migrations
   npm run db:generate

   # Push schema to database
   npm run db:push
   ```

   Using pnpm:
   ```bash
   pnpm db:generate
   pnpm db:push
   ```

4. **Start development server**

   Using npm:
   ```bash
   npm run dev
   ```

   Using pnpm:
   ```bash
   pnpm dev
   ```

   Open [http://localhost:3000](http://localhost:3000) in your browser.

## 📁 Project Structure

```
src/
 ├── app/              # Next.js App Router
 │   ├── layout.tsx
 │   ├── page.tsx
 │   └── api/          # API routes
 │
 ├── components/       # React components
 │   └── ui/          # shadcn/ui components
 │
 ├── lib/             # Utility functions
 │   ├── db.ts        # Drizzle database client
 │   ├── auth.ts      # Better Auth configuration
 │   ├── utils.ts     # Helper functions
 │   └── validation.ts # Zod schemas
 │
 ├── db/              # Database
 │   ├── schema.ts    # Drizzle schema
 │   └── drizzle.config.ts
 │
 ├── hooks/           # React hooks
 │   └── use-theme.ts
 │
 ├── types/           # TypeScript types
 │   └── index.d.ts
 │
 ├── config/          # App configuration
 │   └── site.ts
 │
 └── styles/          # Global styles
     └── globals.css
```

## 🛠️ Available Scripts

All scripts work with npm, pnpm, or yarn. Examples below use npm:

- `npm run dev` - Start development server with Turbopack
- `npm run build` - Build for production
- `npm start` - Start production server
- `npm run lint` - Run ESLint
- `npm run format` - Format code with Prettier
- `npm run db:generate` - Generate Drizzle migrations
- `npm run db:push` - Push schema to database
- `npm run db:studio` - Open Drizzle Studio

**Note:** With pnpm, you can omit `run` (e.g., `pnpm dev` instead of `pnpm run dev`)

## 🐳 Docker Setup

### Development with Docker Compose

```bash
# Start PostgreSQL and app
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

The app will be available at `http://localhost:3000` and PostgreSQL at `localhost:5433`.

## 🔐 Authentication

Better Auth is configured and ready to use. The auth endpoints are available at `/api/auth/*`.

See `src/lib/auth.ts` for configuration. Add your authentication providers and adapters as needed.

## 🗄️ Database

Drizzle ORM is configured with PostgreSQL. Add your schema definitions in `src/db/schema.ts`.

### Example Schema

```typescript
import { pgTable, serial, text, timestamp } from "drizzle-orm/pg-core";

export const users = pgTable("users", {
  id: serial("id").primaryKey(),
  name: text("name").notNull(),
  email: text("email").notNull().unique(),
  createdAt: timestamp("created_at").defaultNow(),
});
```

## 🎨 UI Components

shadcn/ui is configured. Add components using:

```bash
npx shadcn@latest add [component-name]
```

Components will be added to `src/components/ui/`.

## 🌙 Dark Mode

Dark mode is configured with `next-themes`. Use the `useTheme` hook:

```typescript
import { useTheme } from "@/hooks/use-theme";

function MyComponent() {
  const { theme, setTheme } = useTheme();
  // ...
}
```

## 📝 Code Quality

- **ESLint** - Linting with Next.js and TypeScript rules
- **Prettier** - Code formatting
- **Husky** - Git hooks for pre-commit linting

## 🚢 Deployment

The project is ready to deploy on platforms like:
- Vercel (recommended for Next.js)
- Railway
- Render
- Any platform supporting Node.js

Make sure to set all environment variables in your deployment platform.

## 📚 Learn More

- [Next.js Documentation](https://nextjs.org/docs)
- [Drizzle ORM](https://orm.drizzle.team/)
- [Better Auth](https://www.better-auth.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [Tailwind CSS](https://tailwindcss.com/)

## 📄 License

MIT

