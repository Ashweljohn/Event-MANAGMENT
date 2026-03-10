# EventHub – Event Management & Booking System

A fully-featured Angular 19 single-page application for browsing, managing, and booking events. Built with Angular Material UI and a clean white theme.

---

## Tech Stack

- **Framework:** Angular 19 (Standalone Components)
- **Language:** TypeScript 5.8
- **UI Library:** Angular Material 19
- **Styling:** CSS + Angular Material White Theme
- **State Management:** RxJS BehaviorSubject & Observables
- **Forms:** Reactive Forms + Template-driven Forms

---

## Features

- Browse events with search, category filter, and sort options
- View detailed event information with seat availability
- User authentication (mock login/logout)
- Book tickets with full form validation
- Material Dialog booking confirmation popup
- My Bookings page with cancel functionality
- Route guards to protect booking pages
- Custom pipes for filtering and sorting events
- Custom directives for featured and sold-out events
- Responsive design for mobile and desktop
- Angular Material components throughout (cards, snackbars, spinners, dialogs, menus)

---

## Project Structure

```
src/
└── app/
    ├── components/
    │   ├── navbar/                  # Top navigation bar
    │   ├── event-list/              # Homepage – browse all events
    │   ├── event-detail/            # Single event detail page
    │   ├── booking-form/            # Ticket booking form + confirmation dialog
    │   ├── my-bookings/             # User's booking history
    │   └── login/                   # Login page
    ├── services/
    │   ├── event.service.ts         # Event data, booking logic (Observables)
    │   └── auth.service.ts          # Mock authentication (BehaviorSubject)
    ├── guards/
    │   └── auth.guard.ts            # Protects /book and /my-bookings routes
    ├── pipes/
    │   ├── filter-events.pipe.ts    # Filters events by search + category
    │   └── sort-events.pipe.ts      # Sorts events by price / date / seats
    ├── directives/
    │   ├── featured-highlight.directive.ts   # Highlights featured event cards
    │   └── sold-out.directive.ts             # Dims sold-out events
    └── models/
        ├── event.model.ts           # Event interface
        ├── booking.model.ts         # Booking interface
        ├── user.model.ts            # User interface
        ├── person.model.ts          # Abstract Person class + RegisteredUser
        └── user-class.model.ts      # UserClass with helper methods
```

---

## Routes

| Path | Component | Guard |
|------|-----------|-------|
| `/events` | EventListComponent | None |
| `/event/:id` | EventDetailComponent | None |
| `/book/:id` | BookingFormComponent | Auth required |
| `/my-bookings` | MyBookingsComponent | Auth required |
| `/login` | LoginComponent | None |

---

## Setup & Installation

### Prerequisites

- Node.js v18 or higher
- npm v9 or higher

### Steps

**1. Clone or extract the project folder**

```bash
cd enhanced-event-system
```

**2. Install dependencies**

```bash
npm install
```

**3. Start the development server**

```bash
ng serve -o
```

The app will open automatically at **http://localhost:4200**

---

## Demo Login

The app uses mock authentication. Use any of these to log in:

| Email | Password |
|-------|----------|
| any@email.com | any password (min 6 chars) |

Example:
- Email: `user@demo.com`
- Password: `demo123`

---

## Angular Concepts Covered

### 1. TypeScript Foundations
- Interfaces: `Event`, `User`, `Booking`
- Abstract class: `Person` with `RegisteredUser` subclass
- Class with methods: `UserClass`
- Strong typing throughout all services and components

### 2. Component Architecture
- Standalone components with explicit imports
- Input/Output bindings
- `*ngFor`, `*ngIf`, `[ngClass]`, `[ngStyle]` directives
- `async` pipe for Observable streams in templates

### 3. Routing & Navigation
- Lazy-loaded routes using `loadComponent`
- Route parameters (`/event/:id`, `/book/:id`)
- `ActivatedRoute` for reading route params
- `Router` for programmatic navigation
- Auth guard (`canActivate`) on protected routes
- `withViewTransitions()` for smooth page transitions

### 4. Services & Dependency Injection
- `EventService` – central data store with Observable methods
- `AuthService` – login/logout state via `BehaviorSubject`
- Services injected via constructor DI across components
- `bookings$` Observable for real-time booking updates

### 5. Forms & Validation
- **Reactive Form** in BookingFormComponent:
  - `FormBuilder`, `FormGroup`, `Validators`
  - Required, minLength, email, pattern (phone regex), min/max
  - `markAllAsTouched()` for showing all errors on submit
- **Template-driven Form** in LoginComponent:
  - `[(ngModel)]` two-way binding
  - Inline validation messages

### 6. Custom Pipes & Directives
- `filterEvents` pipe – search term + category filter
- `sortEvents` pipe – price (asc/desc), date, seat count
- `featuredHighlight` directive – adds CSS class to featured cards
- `soldOut` directive – dims elements when seats = 0
- Built-in pipes used: `date`, `number`, `titlecase`, `async`, `slice`, `currency`

### 7. Angular Material UI
- `MatToolbar` – navbar
- `MatCard` – event and booking cards
- `MatFormField` + `MatInput` – all form fields
- `MatButton` – all buttons
- `MatIcon` – icons throughout
- `MatDialog` – booking confirmation popup
- `MatSnackBar` – success/error toast messages
- `MatSpinner` – loading indicators
- `MatSelect` – sort dropdown
- `MatMenu` – user account dropdown
- `MatBadge` – booking count on navbar icon
- `MatDivider` – section separators
- `MatChips` – category filter chips

### 8. Observables & RxJS
- All `EventService` methods return `Observable<T>`
- `BehaviorSubject` for auth state and bookings list
- `delay()` operator to simulate async API calls
- `map()` operator for transforming streams
- `async` pipe in templates to auto-subscribe/unsubscribe

### 9. Integration
- End-to-end flow: Browse → Detail → Login → Book → My Bookings
- Booking cancellation restores available seats in real time
- Shared state via services across all components
- Responsive layout using CSS Grid

---

## Build for Production

```bash
ng build
```

Output will be in the `dist/event-booking-system/` folder.

---

## Known Limitations

- Data is stored in memory only (resets on page refresh)
- Authentication is mocked – no real backend
- No persistent storage (can be extended with localStorage or a REST API)

---

## Developed For

**Project 5 – Event Management and Booking System**  
Course: Angular & TypeScript Front-End Development  
Approaches Covered: 1 through 9
