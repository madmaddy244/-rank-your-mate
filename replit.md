# Student Performance Ranking Application

## Overview

This is a full-stack web application for tracking and visualizing student academic performance based on marks and attendance. The application provides interactive dashboards with charts, leaderboards, and performance analytics to compare students and identify performance levels.

**Core Purpose**: Enable users to add students with their academic metrics (marks and attendance), automatically rank them based on combined performance scores, and visualize the data through multiple views including cards, tables, and interactive charts.

**Tech Stack**:
- **Frontend**: React with TypeScript, Vite build tool
- **UI Framework**: Shadcn/ui components with Radix UI primitives, Tailwind CSS
- **Backend**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **State Management**: TanStack Query (React Query)
- **Charting**: Recharts library

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Component-Based Design**: The application follows a modular React component architecture with clear separation of concerns:

- **UI Components** (`client/src/components/ui/`): Reusable Shadcn/ui components built on Radix UI primitives providing accessible, themeable building blocks
- **Feature Components** (`client/src/components/`): Domain-specific components for student data visualization
- **Pages** (`client/src/pages/`): Route-level components (Dashboard as main view, NotFound for error handling)

**Design System**: Material Design-inspired approach with emphasis on data visualization:
- Custom color palette with light/dark mode support
- Performance-level color coding (excellent: green, good: amber, average: orange, poor: red)
- Inter font family for optimal readability in data contexts
- Consistent spacing using Tailwind's scale (4, 6, 8, 12, 16)

**State Management Strategy**:
- TanStack Query for server state with optimistic updates
- Local component state for UI interactions
- Custom hooks for reusable logic (mobile detection, toast notifications)

**Routing**: Wouter library for lightweight client-side routing

### Backend Architecture

**Server Framework**: Express.js with TypeScript in ESM module format

**API Design**: RESTful API with the following endpoints:
- `GET /api/students` - Fetch all students with calculated ranks
- `GET /api/students/:id` - Fetch single student with rank
- `POST /api/students` - Create new student
- `PATCH /api/students/:id` - Update student data
- `DELETE /api/students/:id` - Remove student

**Business Logic**:
- Ranking algorithm calculates combined score as average of marks and attendance
- Performance levels determined by thresholds: excellent (90%+), good (70-89%), average (50-69%), poor (<50%)
- Ranking recalculated on every data change to maintain accuracy

**Data Validation**: Zod schemas with Drizzle integration for type-safe validation at API boundaries

**Storage Abstraction**: Interface-based storage layer (`IStorage`) allowing for multiple implementations:
- `MemStorage` for in-memory development/testing
- Designed to support database implementations (PostgreSQL with Drizzle ORM)

### Data Storage

**Database Schema** (`shared/schema.ts`):
```
students table:
- id: varchar (UUID primary key)
- name: text (required)
- marks: integer (0-100, required)
- attendance: integer (0-100, required)
```

**ORM**: Drizzle ORM configured for PostgreSQL with:
- Schema definition in TypeScript
- Type-safe queries
- Migration support via `drizzle-kit`
- Connection via `@neondatabase/serverless` for serverless PostgreSQL

**Data Enrichment**: Base student data is enriched with calculated fields:
- `combinedScore`: Average of marks and attendance
- `rank`: Position in sorted list by combined score
- `performanceLevel`: Categorization based on combined score

### External Dependencies

**Database Services**:
- PostgreSQL (configured for Neon serverless)
- Connection string via `DATABASE_URL` environment variable

**UI Component Libraries**:
- Radix UI primitives (accordion, dialog, dropdown, etc.) for accessible components
- Recharts for data visualization (scatter charts, bar charts)
- Embla Carousel for carousel functionality
- Lucide React for consistent iconography

**Development Tools**:
- Vite for fast development and optimized builds
- Replit-specific plugins for dev banner, cartographer, and runtime error handling
- TSX for TypeScript execution in development
- ESBuild for production server bundling

**Styling**:
- Tailwind CSS for utility-first styling
- PostCSS with Autoprefixer
- CSS custom properties for theme variables

**Form Handling**:
- React Hook Form for form state management
- Hookform/resolvers for Zod schema integration

**API Integration**:
- Native Fetch API with custom wrapper for error handling
- TanStack Query for caching, optimistic updates, and request management

**Session Management**: Connect-pg-simple for PostgreSQL-backed session storage (dependency present, implementation pending)

**Build & Deployment**:
- Development: Vite dev server with HMR
- Production: Static client build served by Express with Vite middleware in development