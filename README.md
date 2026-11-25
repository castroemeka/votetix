Build a complete, modern, production-ready web platform called **VoteTix**.

VoteTix is a Nigerian-focused platform that combines **event discovery, online ticket purchasing, digital tickets, QR-code event check-in, online voting, paid voting, organizer management, and administrator management** in one system.

The platform should feel like a premium commercial product rather than a basic template. It should be highly responsive, fast, accessible, secure, visually polished, and easy to navigate on desktop, tablet, and mobile.

## 1. CORE TECHNOLOGY

Use a modern full-stack architecture.

### Frontend
Use:
- HTML5/CSS3/JavaScript or React/Next.js
- Modern responsive CSS
- Reusable components
- Mobile-first design
- Accessible semantic HTML
- Smooth animations and transitions
- Lazy loading for images/videos
- Proper loading, empty, success and error states

### Backend
Use:
- Node.js
- Express.js
- REST API
- PostgreSQL
- Prisma ORM
- JWT authentication
- bcrypt password hashing
- Role-based authorization

### Payments
Integrate **Paystack** for Nigerian payments.

Support:
- Card payments
- Bank transfer
- USSD where available
- Payment initialization
- Payment verification
- Webhooks
- Failed payments
- Successful payments
- Refund-ready architecture
- Transaction references
- Payment history

Never expose the Paystack secret key in frontend code.

### QR
Use QR codes for:
- Digital event tickets
- Ticket verification
- Event check-in

---

# 2. BRAND / VISUAL DESIGN

Create a premium entertainment and technology aesthetic.

Brand name:

**VoteTix**

Tagline:

**Vote. Attend. Experience.**

Design direction:
- Modern
- Premium
- Bold
- Clean
- Energetic
- Youthful
- Professional
- Nigerian/African event-oriented

Use:
- Large cinematic hero sections
- Event photography
- Contest/voting imagery
- Modern cards
- Glass/gradient effects where appropriate
- Subtle shadows
- Rounded corners
- Strong typography
- Smooth hover effects
- Micro-interactions
- Animated counters
- Modern buttons
- Skeleton loaders

Use a consistent design system throughout the entire application.

Do not make the website look like a generic admin template.

---

# 3. MAIN PUBLIC WEBSITE

Create the following pages.

## Homepage

Create a visually impressive homepage containing:

### Header
Logo:
**VoteTix**

Navigation:
- Home
- Events
- Vote
- How It Works
- About
- Contact

Buttons:
- Login
- Create Account

On mobile:
- Use a functional hamburger menu
- Menu should animate open/close
- Navigation should work correctly
- Clicking outside the menu should close it
- Escape key should close it

### Hero section

Create a large cinematic hero section.

Headline:

**Vote. Attend. Experience.**

Supporting text explaining that users can discover events, buy tickets and vote for their favourite contestants.

Primary CTA:
**Explore Events**

Secondary CTA:
**Start Voting**

Include:
- Event imagery
- Subtle animations
- Floating event cards
- Voting statistics
- Ticket visual
- Responsive layout

Do not allow additional sections or carousels to visually break the hero layout.

### Featured Events

Show event cards containing:
- Event image
- Event name
- Date
- Time
- Location
- Ticket price
- Category
- Available tickets
- Organizer
- "View Event" button
- "Buy Ticket" button

Categories:
- Music
- Concert
- Comedy
- Conference
- Sports
- Festival
- Fashion
- Entertainment
- Other

### Trending Events

Show popular events based on:
- Ticket sales
- Views
- Recent activity

### Voting Contests

Show active contests.

Each card should contain:
- Contest image
- Contest name
- Number of contestants
- Voting deadline
- Current status
- "View Contest"
- "Vote Now"

### How It Works

Show three/four steps:

1. Discover an event
2. Buy your ticket
3. Receive your digital QR ticket
4. Attend or vote

### Statistics section

Display animated statistics such as:
- Events hosted
- Tickets sold
- Votes cast
- Registered users

### Testimonials

Include customer testimonials.

### Newsletter

Allow users to subscribe to updates.

### Footer

Include:
- Logo
- Navigation
- Social links
- Contact information
- Terms
- Privacy Policy
- Refund Policy
- FAQ

---

# 4. EVENT DISCOVERY

Create `/events`.

Features:

- Search events
- Filter by category
- Filter by location
- Filter by date
- Filter by price
- Sort by popularity
- Sort by newest
- Sort by price
- Pagination or infinite scrolling

Event cards should be responsive.

Create an event details page:

`/events/:slug`

Include:
- Large event banner
- Event title
- Date
- Time
- Venue
- Address
- Google Maps/location link
- Organizer
- Description
- Event images
- Event video
- Ticket types
- Ticket prices
- Ticket availability
- Quantity selector
- Buy ticket button
- Share button
- Related events

---

# 5. TICKET PURCHASE SYSTEM

Build a complete ticket checkout system.

Ticket types:
- Regular
- VIP
- VVIP
- Early Bird
- Group Ticket
- Custom ticket types

Each ticket type should support:
- Name
- Description
- Price
- Quantity available
- Sale start
- Sale end
- Maximum tickets per customer

Checkout should collect:
- Name
- Email
- Phone number
- Ticket quantity

Calculate:
- Subtotal
- Service fee
- Total

Before payment show an order summary.

Then initialize Paystack payment.

After payment:
- Verify transaction
- Show payment result
- Create order
- Generate ticket
- Generate unique ticket code
- Generate QR code
- Send confirmation-ready response

---

# 6. DIGITAL TICKETS

Create a beautiful digital ticket page.

Each ticket should contain:
- VoteTix logo
- Event name
- Event date
- Venue
- Ticket type
- Customer name
- Ticket code
- QR code
- Order number
- Purchase date
- Ticket status

Ticket statuses:
- Valid
- Used
- Cancelled
- Expired

Allow:
- View ticket
- Display QR code
- Print ticket
- Download/print-friendly ticket

---

# 7. QR CHECK-IN SYSTEM

Create an organizer/scanner interface.

Scanner page:

`/scanner`

Allow authorized staff to scan QR codes using the device camera.

After scanning:
- Validate ticket
- Show attendee name
- Show event
- Show ticket type
- Show ticket status

If valid:
Show a large success message:

**Ticket Valid**

Then mark ticket as:
**USED**

If already used:

**Ticket Already Used**

If invalid:

**Invalid Ticket**

Record:
- Scanner
- Date
- Time
- Ticket
- Event
- Result

Prevent duplicate check-ins.

---

# 8. E-VOTING SYSTEM

Create a dedicated voting platform.

Page:

`/vote`

Show:
- Active contests
- Upcoming contests
- Closed contests

Contest page:

`/vote/:slug`

Show:
- Contest banner
- Contest name
- Description
- Rules
- Voting deadline
- Number of contestants
- Voting price
- Voting status
- Contestants

Contestant cards:
- Photo
- Name
- Contestant number
- Biography
- Vote count where appropriate
- Vote button

---

# 9. PAID VOTING

Allow users to purchase votes.

Example:

Contestant:
**Contestant #07 – Amaka Johnson**

Voting packages:

1 Vote — ₦100
5 Votes — ₦500
10 Votes — ₦1,000
25 Votes — ₦2,500
50 Votes — ₦5,000
100 Votes — ₦10,000

Allow custom quantities if enabled.

Calculate:
- Number of votes
- Price per vote
- Total

Then process payment through Paystack.

After successful payment:
- Verify Paystack transaction
- Record vote transaction
- Add votes to contestant
- Store payment reference
- Record timestamp
- Prevent fraudulent duplicate transactions

Create a vote confirmation screen.

---

# 10. VOTING LEADERBOARD

Create a live leaderboard.

Show:
- Position
- Contestant
- Photo
- Votes
- Percentage
- Progress bar

Example:

1. Amaka Johnson — 12,540 votes
2. Grace Williams — 10,420 votes
3. Chidinma Peter — 8,900 votes

Leaderboard should update dynamically.

Highlight:
- Current leader
- User's selected contestant
- Vote closing time

Do not expose sensitive transaction data publicly.

---

# 11. USER AUTHENTICATION

Create:

`/login`

`/register`

`/forgot-password`

`/reset-password`

Authentication features:
- Email/password registration
- Login
- Logout
- JWT authentication
- Password hashing
- Password reset architecture
- Account validation
- Protected routes

User roles:

### USER
Can:
- Browse events
- Purchase tickets
- View tickets
- Vote
- View vote history
- Manage profile

### ORGANIZER
Can:
- Create events
- Edit events
- Publish events
- Create ticket types
- View orders
- View attendees
- View sales
- Scan tickets
- Create voting contests
- Manage contestants
- View voting statistics

### ADMIN
Can:
- Manage users
- Manage organizers
- Manage events
- Manage contests
- Manage payments
- View platform analytics
- Suspend accounts
- Approve organizers
- Manage categories
- View audit logs

### SCANNER
Can:
- Scan tickets
- View check-in history
- Verify tickets

---

# 12. USER DASHBOARD

Create `/dashboard`.

Sections:

### Overview
Show:
- Total tickets
- Upcoming events
- Past events
- Votes made
- Orders
- Recent activity

### My Tickets
Show all purchased tickets.

### My Orders
Show:
- Order number
- Event
- Amount
- Date
- Payment status

### My Votes
Show:
- Contest
- Contestant
- Number of votes
- Amount paid
- Date

### Profile
Allow:
- Edit name
- Edit email
- Edit phone
- Change password
- Profile image

---

# 13. ORGANIZER DASHBOARD

Create a professional dashboard.

Sidebar:

- Overview
- Events
- Create Event
- Orders
- Attendees
- Ticket Scanner
- Voting Contests
- Contestants
- Payments
- Analytics
- Settings

Overview should display:

- Total revenue
- Tickets sold
- Tickets remaining
- Total events
- Total attendees
- Total votes
- Active contests

Add charts:
- Revenue over time
- Ticket sales
- Attendance
- Voting activity

---

# 14. CREATE EVENT

Create a full event creation form.

Fields:
- Event name
- Slug
- Description
- Category
- Cover image
- Gallery images
- Event video
- Date
- Start time
- End time
- Venue
- Address
- City
- State
- Ticket types
- Prices
- Ticket quantity
- Sales start
- Sales end
- Maximum tickets per customer

Allow organizers to:
- Save draft
- Preview
- Publish
- Unpublish
- Cancel

Validate all fields.

---

# 15. ORGANIZER ORDER MANAGEMENT

Create an order management page.

Show:
- Order number
- Customer
- Event
- Ticket type
- Quantity
- Amount
- Payment status
- Date

Add:
- Search
- Filter
- Sort
- Pagination

Allow export-ready structure for CSV reports.

---

# 16. ATTENDEE MANAGEMENT

Create an attendee page.

Show:
- Name
- Email
- Phone
- Ticket
- Ticket type
- Check-in status
- Purchase date

Filters:
- Checked in
- Not checked in
- Ticket type

---

# 17. ADMIN PANEL

Create `/admin`.

Admin dashboard should contain:

### Platform overview
- Total users
- Organizers
- Events
- Tickets sold
- Revenue
- Votes
- Active contests

### User management
- Search users
- Filter roles
- Activate/deactivate
- Change roles
- View account

### Event management
- Approve events
- Reject events
- Publish/unpublish
- Delete events

### Contest management
- Approve contests
- Manage contestants
- Monitor votes

### Payment management
- Transactions
- Successful payments
- Failed payments
- Refund-ready workflow

### Audit logs
Record important administrative actions.

---

# 18. DATABASE

Use PostgreSQL with Prisma.

Create models for:

- User
- Event
- TicketType
- Order
- OrderItem
- Ticket
- TicketScan
- VotingContest
- Contestant
- VoteTransaction
- Vote
- Payment
- AuditLog
- Notification
- NewsletterSubscriber

Include:
- IDs
- timestamps
- relationships
- indexes
- unique constraints
- status enums
- proper foreign keys

Use database transactions where money or ticket inventory is involved.

Prevent overselling tickets using transactional stock checks.

---

# 19. API

Create REST endpoints such as:

Authentication:
- POST `/api/auth/register`
- POST `/api/auth/login`
- GET `/api/me`

Events:
- GET `/api/events`
- GET `/api/events/:slug`
- POST `/api/events`
- PATCH `/api/events/:id`
- DELETE `/api/events/:id`

Tickets:
- POST `/api/payments/ticket/initialize`
- GET `/api/my/tickets`
- GET `/api/tickets/:code/qr`
- POST `/api/tickets/scan`

Voting:
- GET `/api/voting`
- GET `/api/voting/:slug`
- POST `/api/voting`
- POST `/api/payments/vote/initialize`

Payments:
- POST `/api/payments/verify`
- POST `/api/payments/webhook`

Organizer:
- GET `/api/organizer/overview`

Admin:
- GET `/api/admin/overview`
- GET `/api/admin/users`
- GET `/api/admin/events`
- GET `/api/admin/payments`

Protect all private endpoints with JWT and role-based authorization.

---

# 20. PAYSTACK WEBHOOK SECURITY

Implement proper Paystack webhook handling.

Verify the webhook signature using the Paystack secret key.

Never trust frontend payment success messages.

Always verify payment server-side.

When payment succeeds:
1. Verify transaction
2. Verify amount
3. Verify reference
4. Check transaction has not already been processed
5. Mark payment successful
6. Create order/tickets or votes
7. Commit database transaction
8. Return success

Make payment processing idempotent.

---

# 21. SECURITY

Implement:

- bcrypt password hashing
- JWT authentication
- Role-based authorization
- Input validation using Zod
- SQL injection protection through Prisma
- XSS-safe rendering
- CORS configuration
- Rate limiting
- Secure HTTP headers
- Environment variables
- Server-side payment verification
- Webhook signature verification
- Duplicate payment protection
- Ticket ownership verification
- Voting fraud protection
- Audit logs

Never expose:
- JWT secret
- Database password
- Paystack secret key

---

# 22. RESPONSIVE DESIGN

The website must work perfectly on:

- 320px mobile
- 375px mobile
- 414px mobile
- 768px tablet
- 1024px tablet/laptop
- 1280px desktop
- 1440px desktop
- 1920px large desktop

Pay particular attention to:

- Navigation
- Hamburger menu
- Dashboard sidebar
- Tables
- Event cards
- Checkout
- Voting cards
- QR tickets
- Forms
- Modals
- Charts

No horizontal scrolling on mobile unless explicitly required.

The mobile hamburger button must actually work.

---

# 23. SEARCH / FILTERING

Implement functional search.

Events:
- Search by title
- Category
- Location
- Date
- Price

Voting:
- Search contests
- Search contestants

Admin:
- Search users
- Search events
- Search transactions

Organizer:
- Search attendees
- Search orders
- Search tickets

---

# 24. NOTIFICATIONS

Create a notification system ready for:

- Ticket purchase confirmation
- Payment confirmation
- Event reminders
- Voting confirmation
- Contest closing reminders
- Organizer notifications
- Admin notifications

Design the system so email/SMS providers can be connected later.

---

# 25. CONTACT PAGE

Create a professional contact page.

Display:

Email:
youngjosh@gmail.com

Phone:
07068561623
09037436800

Office:
Shop 034, Swissgarden Plaza,
450 Ogui Road,
opposite Otigba Garden,
Enugu, Nigeria.

Include:
- Contact form
- Name
- Email
- Phone
- Subject
- Message
- Submit button

The contact form should have a backend endpoint and validation.

---

# 26. ABOUT PAGE

Explain:
- What VoteTix is
- Event ticketing
- E-voting
- Secure payments
- QR verification
- Organizer tools

Include statistics and company values.

---

# 27. LEGAL PAGES

Create:

- Privacy Policy
- Terms & Conditions
- Refund Policy
- Voting Terms
- Cookie Policy

Make them accessible from the footer.

---

# 28. ERROR / EMPTY STATES

Create polished pages/components for:

- 404
- 403
- 500
- No events found
- No tickets
- No orders
- No contests
- Payment failed
- Payment pending
- Ticket expired
- Ticket already used
- Unauthorized access

---

# 29. LOADING STATES

Use skeleton loaders for:
- Events
- Voting contests
- Dashboard cards
- Tables
- Tickets
- Contestants

Use spinners or progress indicators during:
- Login
- Registration
- Payment initialization
- Ticket scanning
- Voting
- Form submission

Prevent double submissions.

---

# 30. MEDIA

Create sections supporting:

- Event photos
- Event galleries
- Event videos
- Contestant photos
- Promotional banners

Use optimized responsive images.

Add lazy loading.

Create visually attractive image/video cards.

---

# 31. SEO

Implement:

- Page titles
- Meta descriptions
- Open Graph tags
- Twitter/X cards
- Canonical URLs
- Semantic HTML
- Sitemap
- Robots.txt
- Event structured data where appropriate

Use SEO-friendly event slugs.

---

# 32. PERFORMANCE

Optimize for:

- Fast page loading
- Responsive images
- Lazy loading
- Minified assets
- Efficient database queries
- Pagination
- API caching where appropriate
- Code splitting if using React
- Minimal unnecessary JavaScript

Target excellent Lighthouse scores.

---

# 33. ACCESSIBILITY

Follow WCAG principles.

Include:
- Keyboard navigation
- Focus states
- ARIA labels
- Proper contrast
- Semantic HTML
- Accessible forms
- Accessible modals
- Screen-reader friendly navigation

---

# 34. DEMO DATA

Create realistic demo data.

Events:
- Afrobeats Night 2026
- Tech Innovation Summit
- Port Harcourt Comedy Festival
- Nigerian Fashion Week
- Startup & Business Expo

Voting contests:
- Miss Rivers 2026
- Campus Personality Awards
- Best Emerging Artist

Create sample contestants and ticket types.

---

# 35. PROJECT STRUCTURE

Use a clean professional structure.

Example:

```text
votetix/
├── frontend/
│   ├── pages/
│   ├── components/
│   ├── assets/
│   └── styles/
├── server/
│   ├── routes/
│   ├── controllers/
│   ├── middleware/
│   ├── services/
│   └── utils/
├── prisma/
│   ├── schema.prisma
│   └── seed.js
├── public/
├── uploads/
├── .env.example
├── package.json
├── README.md
└── API.md
```

Keep the code modular and maintainable.

---

# 36. FRONTEND API INTEGRATION

Do not create fake buttons.

Every major action must actually connect to the backend.

Examples:

"Buy Ticket"
→ checkout
→ Paystack
→ payment verification
→ order creation
→ ticket generation

"Vote"
→ vote quantity
→ payment
→ verification
→ vote recorded
→ leaderboard updated

"Scan Ticket"
→ camera
→ QR code
→ API verification
→ ticket status
→ check-in recorded

"Create Event"
→ form
→ validation
→ API
→ database
→ organizer dashboard

"Login"
→ API
→ JWT
→ session
→ redirect based on role

---

# 37. UX REQUIREMENTS

Make the website feel like a real commercial platform.

Include:
- Toast notifications
- Confirmation dialogs
- Smooth page transitions
- Hover states
- Button loading states
- Form validation
- Inline error messages
- Success messages
- Empty states
- Breadcrumbs where useful
- Sticky checkout summary
- Responsive navigation

Do not leave dead links.

Every navigation item must lead somewhere meaningful.

---

# 38. IMPORTANT BUSINESS RULES

Tickets:
- Do not allow purchase beyond available inventory.
- Do not issue tickets until payment is confirmed.
- Each ticket gets a unique code.
- Each ticket gets a unique QR code.
- A used ticket cannot be reused.

Voting:
- Do not count votes until payment is confirmed.
- Do not trust frontend vote counts.
- Verify every payment server-side.
- Prevent duplicate processing.
- Respect contest start/end times.
- Do not allow voting on closed contests.

Payments:
- Never expose secret keys.
- Verify amount and reference.
- Make webhook processing idempotent.
- Store payment references.

---

# 39. ADMIN ANALYTICS

Create charts showing:

- Revenue
- Ticket sales
- Votes
- Active users
- Events
- Orders
- Payment success/failure
- Attendance

Use clean modern charts.

Allow date filtering:
- Today
- 7 days
- 30 days
- 90 days
- Custom

---

# 40. FINAL REQUIREMENT

Do not generate only a UI mockup.

Build a functioning full-stack application.

All major buttons, forms, authentication, APIs, database operations, payment flows, ticket generation, QR verification, voting, dashboards and navigation must work.

Use realistic demo data.

Do not leave TODO placeholders for core features.

If a third-party service cannot be fully configured without credentials, implement the complete integration architecture and clearly identify only the environment variables that need to be supplied.

Create:
- complete source code
- database schema
- seed data
- API documentation
- environment example
- README
- setup instructions
- development instructions
- production deployment instructions

The final result should be a polished, scalable **VoteTix event ticketing + e-voting platform** suitable for further production development.

Before finishing:
1. Check all routes.
2. Check all links.
3. Check mobile navigation.
4. Check responsive layouts.
5. Check authentication.
6. Check authorization.
7. Check database relationships.
8. Check payment flow.
9. Check ticket generation.
10. Check QR scanning.
11. Check voting flow.
12. Check admin dashboard.
13. Check organizer dashboard.
14. Check error handling.
15. Check for broken JavaScript.
16. Check for console errors.
17. Check for missing assets.
18. Check for mobile overflow.
19. Check that no secrets are hardcoded.
20. Provide exact commands for installation and deployment.

Do not remove existing functionality when adding new features. Preserve working features and improve them where necessary.
