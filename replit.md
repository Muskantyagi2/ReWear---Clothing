# ReWear - Sustainable Fashion Swapping Platform

## Overview

ReWear is a sustainable fashion swapping platform that enables users to exchange clothing items through a point-based system. The application combines clothing marketplace functionality with social features, allowing users to trade items directly or use points for redemption. Built with a modern full-stack architecture using React, Express, and PostgreSQL.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Framework**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom design system
- **State Management**: TanStack Query (React Query) for server state
- **Form Handling**: React Hook Form with Zod validation
- **Build Tool**: Vite with custom configuration

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with Neon serverless PostgreSQL
- **Authentication**: Session-based auth with express-session and bcrypt
- **Session Storage**: PostgreSQL session store (connect-pg-simple)
- **API Design**: RESTful API with JSON responses

### Data Storage
- **Primary Database**: PostgreSQL (Neon serverless)
- **ORM**: Drizzle ORM with type-safe schema definitions
- **Migrations**: Drizzle Kit for schema management
- **Session Storage**: PostgreSQL-backed sessions

## Key Components

### Database Schema
Located in `shared/schema.ts`, the database includes:
- **Users**: Authentication, profile data, points system
- **Items**: Clothing listings with categories, conditions, approval system
- **Swap Requests**: Item exchanges and point-based transactions
- **Notifications**: Real-time user communications

### Authentication System
- Session-based authentication with secure password hashing
- User registration and login flows
- Protected routes with middleware
- Admin role system for content moderation

### Item Management
- Multi-category clothing system (shirts, pants, shoes, etc.)
- Condition-based pricing (Like New, Excellent, Good, Fair)
- Image upload support via URLs
- Admin approval workflow for quality control
- Tagging system for better discoverability

### Swap/Transaction System
- Two-way item swapping between users
- Point-based redemption system
- Request workflow (pending, accepted, rejected, completed)
- Message system for swap negotiations

### UI/UX Design
- Earth-toned color scheme reflecting sustainability focus
- Mobile-responsive design with Tailwind CSS
- Component library based on shadcn/ui and Radix primitives
- Accessible design patterns throughout

## Data Flow

1. **User Registration/Login**: 
   - User submits credentials
   - Server validates and creates session
   - Client receives user data and stores in query cache

2. **Item Listing**:
   - User submits item details with images
   - Server validates data and creates pending item
   - Admin reviews and approves items
   - Approved items appear in marketplace

3. **Swap Process**:
   - User browses items and initiates swap request
   - Owner receives notification and can accept/reject
   - Upon acceptance, items change status and points transfer
   - Both parties receive confirmation notifications

4. **Real-time Updates**:
   - React Query manages cache invalidation
   - Notifications update automatically
   - Item status changes reflect immediately

## External Dependencies

### Core Framework Dependencies
- **React Ecosystem**: React 18, React DOM, React Hook Form
- **Routing**: Wouter for lightweight client-side routing
- **UI Components**: Radix UI primitives, shadcn/ui components
- **Styling**: Tailwind CSS, class-variance-authority, clsx
- **State Management**: TanStack Query for server state management

### Backend Dependencies
- **Database**: Neon serverless PostgreSQL, Drizzle ORM
- **Authentication**: bcrypt for password hashing, express-session
- **Validation**: Zod for runtime type checking
- **Development**: tsx for TypeScript execution, esbuild for bundling

### Development Tools
- **Build Tools**: Vite for frontend bundling, esbuild for backend
- **Type Checking**: TypeScript with strict configuration
- **CSS Processing**: PostCSS with Tailwind and Autoprefixer
- **Development Server**: Custom Vite middleware setup

## Deployment Strategy

### Build Process
- Frontend builds to `dist/public` using Vite
- Backend bundles to `dist/index.js` using esbuild
- Static assets served from built frontend directory

### Environment Configuration
- Database connection via `DATABASE_URL` environment variable
- Session management with PostgreSQL store
- Development/production environment detection

### Development Workflow
- Hot module replacement via Vite in development
- TypeScript compilation checking without emission
- Database schema changes via Drizzle migrations
- Session-based development state persistence

### Production Considerations
- Static file serving handled by Express in production
- Session storage in PostgreSQL for scalability
- Error handling middleware for API endpoints
- CORS and security middleware for production deployment

The application follows a monorepo structure with shared types and schemas, enabling type safety across the full stack while maintaining clear separation of concerns between frontend and backend logic.