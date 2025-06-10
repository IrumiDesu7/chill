# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Type checking
npm run check
npm run check:watch  # Watch mode

# Linting and formatting
npm run lint         # Check formatting with Prettier and lint with ESLint
npm run format       # Auto-format code with Prettier

# Database management
npm run db:push      # Push schema changes to database
npm run db:migrate   # Run database migrations
npm run db:studio    # Open Drizzle Studio for database management
```

## Architecture Overview

This is a SvelteKit application with the following key components:

### Tech Stack

- **Framework**: SvelteKit with Svelte 5
- **Styling**: Tailwind CSS v4 with tailwind-merge and tailwind-variants
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Custom session-based auth implementation
- **Deployment**: Vercel adapter
- **shadcn-svelte**: Re-usable components built with Bits UI and Tailwind CSS. (https://www.shadcn-svelte.com/docs)

### Project Structure

- `/src/routes/` - SvelteKit pages and server endpoints
- `/src/lib/server/` - Server-side code (auth, database)
- `/src/lib/server/db/` - Database schema and connection
- `/src/lib/` - Shared utilities and components

### Key Implementation Details

**Database Schema** (`src/lib/server/db/schema.ts`):

- User table with id, username, passwordHash, and optional age
- Session table for authentication with expiration tracking

**Authentication** (`src/lib/server/auth.ts`):

- Custom session-based authentication using secure tokens
- 30-day session duration with automatic renewal
- Session validation and cookie management functions

**Environment Requirements**:

- `DATABASE_URL` - Required PostgreSQL connection string

### Development Notes

- The project uses pnpm as the package manager
- TypeScript is configured for strict type checking
- ESLint and Prettier are configured for code quality
