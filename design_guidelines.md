# Waste Management App - Design Guidelines

## Design Approach

**Design System Strategy**: Material Design 3 foundation, optimized for civic utility and mobile-first usage. Prioritizes clarity, accessibility, and efficient task completion for diverse user base (commuters, citizens, municipal workers).

**Core Principle**: Make environmental action effortless through intuitive interfaces and immediate feedback.

## Layout System

**Spacing Units**: Tailwind spacing of 2, 4, 6, 8, 12, 16, and 20 for consistent rhythm. Container max-width of `max-w-6xl` for content areas, `max-w-2xl` for forms and single-column layouts.

**Grid Strategy**:
- Educational cards: 3-column grid (lg:grid-cols-3 md:grid-cols-2)
- Facility listings: Single column with map integration
- Dashboard stats: 4-column for desktop, 2-column for mobile
- Waste categories: 2-column split for visual learning

## Typography Hierarchy

**Font Stack**: 
- Primary: Roboto or Inter (excellent legibility, accessibility-tested)
- Monospace: Roboto Mono for tracking numbers and codes

**Scale**:
- H1 (Hero/Page): text-4xl lg:text-5xl, font-bold
- H2 (Sections): text-2xl lg:text-3xl, font-semibold
- H3 (Cards/Modules): text-lg lg:text-xl, font-semibold
- Body: text-base, line-height relaxed
- Small (Meta): text-sm, font-medium
- Captions: text-xs, text-gray-600

## Core Components

### Navigation
Bottom navigation bar for mobile (5 icons: Home, Report, Track, Learn, Profile). Desktop: top nav with logo left, main actions center, profile right. Floating action button (FAB) for quick waste reporting, positioned bottom-right with backdrop-blur.

### Hero Section
Full-width hero (h-[500px]) featuring environmental lifestyle photography - person sorting waste correctly with clear bins in clean urban setting, morning light. Overlay with centered quick-action module (backdrop-blur-md):
- "Report Waste" button (primary, large)
- "Find Facility" button (secondary)
- "Track Collection" button (tertiary)
All buttons implement standard hover states, no special interactions on hero.

### Waste Segregation Education Module
Interactive learning cards (rounded-xl, shadow-lg) in 3-column grid:
- Large icon representing category (recyclable, compost, hazardous, general)
- Category name + brief description
- Expandable "Learn More" revealing accepted items list
- Visual examples grid (3x3 thumbnail grid of common items)

### Facility Locator Interface
Split-screen layout:
- Left (w-full lg:w-1/3): Scrollable facility list with cards showing name, distance, operating hours, accepted waste types
- Right (w-full lg:w-2/3): Interactive map with color-coded markers
- Floating search bar overlaying map with location autocomplete
- Filter chips for waste type, open now, distance radius

### Waste Reporting Form
Multi-step card (max-w-2xl, centered) with progress stepper:
- Step 1: Photo upload (camera or gallery, 3 image slots with previews)
- Step 2: Waste category selection (large icon buttons in 2-column grid)
- Step 3: Location pin (map interface with draggable marker)
- Step 4: Optional description (textarea)
- Step 5: Confirmation screen with report number
Success animation upon submission.

### Real-Time Collection Tracker
Map-based interface showing:
- Collection vehicle live position (animated truck icon)
- Planned route polyline
- User's location marker
- ETA countdown timer (large, prominent)
- Status updates timeline (left sidebar on desktop, bottom sheet on mobile)

### Dashboard Cards
Elevated cards (rounded-2xl, border) displaying:
- Personal impact stats: Items recycled, CO2 saved, badges earned
- Upcoming collections: Calendar view with time remaining
- Recent reports: Status badges (pending, resolved, verified)
- Community leaderboard: Top contributors with rankings

### Educational Content Sections
Two-column alternating layouts (image left/right):
- Do's and Don'ts comparison with checkmark/cross icons
- Step-by-step guides with numbered circles
- Impact statistics in large, bold numbers with context
- Video tutorials with play button overlays

### Status Indicators
Color-coded badges (rounded-full, px-3 py-1):
- Green: Verified/Resolved
- Yellow: In Progress
- Red: Urgent/Hazardous
- Blue: Scheduled
Icon + text combinations, use Material Icons.

## Images

**Hero**: Environmental hero showing diverse individual properly sorting waste in clean, modern setting - bright natural lighting, urban/suburban context. Image should inspire action and show correct behavior.

**Educational Sections**: High-quality product photography of waste items categorized correctly - clean backgrounds, clear lighting. Include infographic-style comparison images (before/after proper disposal).

**Success States**: Celebratory illustrations or photos showing clean environments, happy communities, thriving green spaces.

**Facility Photos**: Clean, well-maintained recycling centers and collection points to build trust.

## Interaction Patterns

**Primary Actions**: Large rounded-lg buttons (px-8 py-4) with clear labels. FAB for instant reporting uses rounded-full with icon only.

**Maps**: Interactive with standard pinch-zoom, tap markers for details popup, current location button in corner.

**Cards**: Subtle elevation with hover translate (hover:-translate-y-1, shadow-xl transition).

**Forms**: Rounded-xl inputs with icon prefixes, clear validation states, helper text positioned below.

**Icons**: Material Icons throughout, size-6 standard, size-8 for featured actions, size-10 for category selectors.

**Loading States**: Skeleton screens for lists, spinner for form submissions, animated truck icon for tracking.

## Page Sections (Landing/Marketing)

1. **Hero** with quick actions (h-[500px])
2. **Impact Statistics** (4-column stat grid, py-16)
3. **How It Works** (3-step process with icons, py-20)
4. **Segregation Guide** (interactive category explorer, py-24)
5. **Features Showcase** (alternating image-text, reporting/tracking/learning features, py-20 each)
6. **Community Impact** (testimonials + map of active users, py-20)
7. **Mobile App Preview** (phone mockup screenshots in grid, py-24)
8. **Call to Action** ("Download App" + "Report Online" buttons, py-20)
9. **Footer** with quick links, municipal contact, social media, language selector

**Vertical Rhythm**: py-16 to py-24 for desktop, py-12 for mobile. Maintain breathing room around interactive elements.