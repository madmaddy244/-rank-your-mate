# Design Guidelines: Student Performance Ranking Application

## Design Approach
**Selected System:** Material Design with data visualization focus
**Rationale:** This data-heavy application requires clear information hierarchy, excellent readability, and robust component patterns for displaying comparative statistics and charts.

## Core Design Elements

### A. Color Palette

**Light Mode:**
- Primary: 59 91% 50% (Vibrant blue for trust and focus)
- Background: 0 0% 98% (Soft white)
- Surface: 0 0% 100% (Pure white for cards)
- Text Primary: 220 13% 18%
- Text Secondary: 220 9% 46%

**Dark Mode:**
- Primary: 59 91% 60% (Brighter blue for visibility)
- Background: 222 47% 11% (Deep navy)
- Surface: 217 33% 17% (Elevated navy)
- Text Primary: 210 40% 98%
- Text Secondary: 215 20% 65%

**Performance Indicators:**
- Excellent (90%+): 142 76% 36% (Green)
- Good (70-89%): 43 96% 56% (Amber)
- Average (50-69%): 25 95% 53% (Orange)
- Poor (<50%): 0 84% 60% (Red)

### B. Typography
- **Primary Font:** Inter (Google Fonts) - for excellent readability in data contexts
- **Display Font:** Inter (600-700 weight) for headings
- **Body Text:** Inter (400) at 16px base size
- **Data/Numbers:** Inter (500) at 18px for emphasis
- **Labels:** Inter (500) at 14px, uppercase with letter-spacing

### C. Layout System
**Spacing Units:** Tailwind units of 4, 6, 8, 12, and 16 for consistent rhythm
- Card padding: p-6
- Section spacing: space-y-8
- Component gaps: gap-4 or gap-6
- Container max-width: max-w-7xl

### D. Component Library

**Dashboard Header:**
- App title with icon
- Add friend button (primary CTA)
- View toggle (cards/table)
- Search/filter bar

**Friend Cards:**
- Profile section with avatar (generated initial-based)
- Name and rank badge
- Dual progress bars (marks and attendance)
- Mini bar chart showing both metrics
- Performance indicator dot
- Edit/delete actions

**Leaderboard Table:**
- Sticky header with sortable columns
- Rank badge column (gold/silver/bronze for top 3)
- Name with avatar
- Marks column with visual bar
- Attendance column with visual bar
- Combined score column
- Color-coded row backgrounds based on performance tier

**Charts & Visualizations:**
- Individual performance bar chart (Chart.js or Recharts)
- Scatter plot quadrant chart (X: marks, Y: attendance)
- Performance distribution pie chart
- Trend lines for class average

**Add/Edit Modal:**
- Clean form with labeled inputs
- Real-time validation
- Performance preview as user types
- Success/error states

**Performance Indicators:**
- Color-coded badges
- Icon indicators (check, warning, alert)
- Progress rings for visual appeal

### E. Visual Hierarchy

**Dashboard Layout:**
1. Header with stats summary cards (total friends, average marks, average attendance)
2. Main content area with view toggle
3. Leaderboard/card grid
4. Global performance chart section

**Card Design:**
- Elevated with subtle shadow (shadow-md)
- Rounded corners (rounded-xl)
- Hover state with slight lift (hover:shadow-lg)
- Transition effects for smooth interactions

### F. Data Visualization Guidelines

**Chart Colors:**
- Use performance indicator colors consistently
- Marks: Primary blue
- Attendance: 168 76% 42% (Teal)
- Combined score: 271 91% 65% (Purple)

**Chart Types:**
- Bar charts for individual comparisons
- Scatter plots for correlation analysis
- Donut charts for distribution
- Line overlays for trends

### G. Responsive Behavior
- Desktop (lg): 3-column card grid, full table view
- Tablet (md): 2-column cards, horizontal scroll table
- Mobile: Single column cards, simplified table or cards only

### H. Interaction Patterns
- Smooth transitions (transition-all duration-200)
- Hover effects on interactive elements
- Loading states with skeleton screens
- Success toast notifications for actions
- Confirmation dialogs for deletions

## Images
**No hero image required** - This is a functional dashboard application focused on data display and interaction rather than marketing appeal.

**Icons:** Use Heroicons for consistent, clean iconography throughout (trophy for rankings, chart-bar for stats, user-plus for add action)