# EcoTrack - Smart Waste Management Application

## Overview

EcoTrack is a mobile-first civic waste management application designed to empower citizens to take environmental action through intuitive interfaces. The platform enables users to report waste incidents, locate recycling facilities, track waste collection schedules, and learn proper waste segregation practices. Built with a focus on accessibility and ease of use for diverse user demographics in small cities and tier-2 towns.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React with TypeScript, utilizing Vite as the build tool for fast development and optimized production builds.

**UI Component System**: Shadcn/ui with Radix UI primitives, implementing Material Design 3 principles adapted for civic utility. The design system emphasizes:
- Mobile-first responsive layouts with bottom navigation for mobile devices
- Consistent spacing using Tailwind's standardized units (2, 4, 6, 8, 12, 16, 20)
- Accessibility-first components with ARIA support
- Dark mode capability through CSS variables

**Routing**: Client-side routing using Wouter for lightweight navigation between pages (Home, Education, Facilities, Report, Track, Dashboard).

**State Management**: TanStack Query (React Query) for server state management, providing caching, synchronization, and optimistic updates for data fetching operations.

**Styling**: Tailwind CSS with custom design tokens for colors, spacing, and typography. The color system uses HSL values with CSS variables for theme flexibility.

**Form Handling**: React Hook Form with Zod for schema validation, ensuring type-safe form data throughout the application.

### Backend Architecture

**Server Framework**: Express.js with TypeScript, structured as an ESM module for modern JavaScript compatibility.

**API Design**: RESTful API endpoints following resource-based conventions:
- `/api/facilities` - Recycling facility management
- `/api/collections` - Waste collection scheduling
- `/api/waste-reports` - User-submitted waste reports
- `/api/user-stats` - User engagement metrics

**Data Storage Strategy**: In-memory storage implementation (MemStorage class) providing a storage interface that can be swapped for database persistence without changing application logic. The interface defines clear contracts for CRUD operations on all entities.

**Type Safety**: Shared schema definitions between client and server using Drizzle ORM's schema builder and Zod validation, ensuring end-to-end type consistency.

**Session Management**: Built to support session-based authentication using connect-pg-simple for PostgreSQL session storage (when database is provisioned).

### Data Models

**Core Entities**:
- **Users**: Authentication and profile management
- **Waste Reports**: Categorized waste incidents with geolocation, images, status tracking, and unique report numbers
- **Facilities**: Recycling centers with location data, operating hours, accepted waste types
- **Collections**: Scheduled waste pickups with real-time tracking (area, ETA, vehicle ID)
- **User Stats**: Gamification metrics (reports submitted, points earned, impact tracking)

**Validation Strategy**: Drizzle-Zod integration generates runtime validators from database schemas, providing single source of truth for data structure.

### Database Design

**ORM**: Drizzle ORM configured for PostgreSQL with the Neon serverless adapter for edge-compatible database connections.

**Schema Location**: Centralized in `shared/schema.ts` for client-server sharing.

**Migration Strategy**: Drizzle Kit for schema migrations with push-based deployment (`npm run db:push`).

**Key Design Decisions**:
- UUID primary keys for distributed system compatibility
- Array types for flexible multi-value fields (waste types, images)
- Timestamp tracking for temporal queries and analytics
- Status enums for workflow state management

### Geolocation Features

The application requires device geolocation for:
- Waste report submission with precise coordinates
- Facility proximity search and mapping
- Collection route tracking

Implementation uses browser Geolocation API with fallback handling for permission denial.

### Image Handling

Waste reports support multiple image uploads stored as URL arrays. Current implementation expects base64 or external URLs; production deployment would integrate cloud storage (S3, Cloudinary) for scalable image management.

### Mobile Optimization

**Responsive Strategy**:
- Bottom navigation bar on mobile (< 768px)
- Top navigation on desktop
- Touch-optimized button sizes (min-height approach)
- Viewport-based typography scaling

**Performance**: Code splitting and lazy loading enabled through Vite, with React Query providing intelligent caching to minimize network requests.

## External Dependencies

### UI Component Libraries

**Radix UI**: Headless accessible component primitives (Dialog, Dropdown, Toast, etc.) providing keyboard navigation, focus management, and ARIA attributes out of the box.

**Shadcn/ui**: Pre-styled Radix components with Tailwind CSS, customizable through the design system defined in `components.json`.

**Embla Carousel**: Touch-enabled carousel component for image galleries and educational content.

### Database & ORM

**PostgreSQL**: Primary database (via DATABASE_URL environment variable), chosen for:
- JSON/JSONB support for flexible schemas
- Array types for multi-value fields
- Geospatial capabilities (PostGIS potential)
- ACID compliance for transaction integrity

**Neon Serverless**: PostgreSQL adapter optimized for serverless environments with connection pooling and edge compatibility.

**Drizzle ORM**: TypeScript-first ORM providing:
- SQL-like query builder with full type inference
- Zero-cost abstractions over raw SQL
- Schema-first migrations

### Validation & Type Safety

**Zod**: Runtime schema validation integrated throughout the stack for request validation, form handling, and data parsing.

**TypeScript**: Strict mode enabled for maximum type safety, with path aliases configured for clean imports.

### Developer Experience

**Replit Integration**: 
- Vite plugins for runtime error overlay and dev banner
- Cartographer plugin for code intelligence
- Hot module replacement for instant feedback

**Build Process**:
- Client: Vite bundle to `dist/public`
- Server: esbuild bundle to `dist/index.js`
- Production startup uses compiled artifacts for faster cold starts

### Design Assets

Generated images stored in `attached_assets/generated_images/` for educational content (waste category illustrations).

### Future Integration Points

The architecture anticipates:
- **Real-time Updates**: WebSocket support for live collection tracking
- **Push Notifications**: Service worker registration for offline capability and notifications
- **Analytics**: Event tracking for user engagement metrics
- **Maps Integration**: Google Maps or Mapbox for visual facility location and route display
- **Cloud Storage**: Image CDN for scalable media handling