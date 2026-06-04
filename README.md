# Silent Disco Event Portal

An interactive event registration and admin dashboard platform for the Silent Disco event. This project allows attendees to register for the event, dynamically generates unique tickets, and provides administrators with a secure, real-time dashboard to monitor signups and export data.

## Features

- **Responsive Landing Page**: Rich cyberpunk-inspired visuals introducing event channels, dates, and featured DJs.
- **Form Validation & Anti-Duplicate Protection**: Multi-step registration validation that verifies email uniqueness before allocating tickets.
- **Unique Ticket Generation**: Dynamic, collision-free ticket ID allocation (`SD-2025-{timestamp}-{random6}`) stored in session and rendered on confirmation.
- **Pass Downloads**: Client-side ticket printing/downloads and Add to Calendar (`.ics`) schedules.
- **Secure Admin Dashboard**: 
  - Gated access with password verification (`NOTIONADMIN2025`) and visual pre-render prevention.
  - Real-time statistics counters: Total registrations, Today's signups, Latest attendee name, and Count of unique branches.
  - Interactive "Recent Registrations" bento card showing the top 5 signups with neon style accents.
  - Dynamic records table with local date conversions.
  - Real-time instant search bar (searchable by Name, Email, and Ticket ID).
  - Refresh and CSV Export download tools.

## Admin Dashboard Access

The project includes a protected administrator dashboard for viewing and managing registrations.

### Access Methods

Users can access the Admin Dashboard by:

1. Clicking the profile icon located in the navigation bar on:

   * Home Page
   * Event Info Page
   * Registration Page

OR

2. Opening:

admin.html

directly.

### Administrator Password

Current administrator password:

NOTIONADMIN2025

### Dashboard Capabilities

* View all registrations
* Search registrations by Name
* Search registrations by Email
* Search registrations by Ticket ID
* View registration statistics
* View recent registrations
* Export registration data as CSV

## Security

* Uses Supabase Publishable Key only
* No Secret Keys or Service Role Keys are exposed
* Registration inputs are validated before submission
* Admin Dashboard is password protected
* Supabase Row Level Security policies should be configured for production deployments

## Technologies Used

- **Frontend**: HTML5, Vanilla JavaScript, CSS3
- **CSS Framework**: Tailwind CSS (loaded via CDN)
- **Database / Backend**: Supabase
- **Icons & Typography**: Google Fonts (Anton, Inter, JetBrains Mono), Material Symbols Outlined

## Folder Structure

```
├── assets/                       # Image assets and designs
│   ├── dj_cyan.png               # DJ featured image (Blue Channel)
│   ├── dj_magenta.png            # DJ featured image (Pink Channel)
│   └── dj_neon.png               # DJ featured image (Green Channel)
├── index.html                    # Homepage / Landing page
├── event-info.html               # Event channels details page
├── register.html                 # Registration form page
├── confirmation.html             # Registration success ticket page
├── admin.html                    # Admin Dashboard page
├── supabase.js                   # Supabase client setup script
├── code_event_details.html       # Reference file / original markup
├── code_event_portal.html        # Reference file / original markup
├── code_event_reg_portal.html    # Reference file / original markup
├── code_event_reg_success.html   # Reference file / original markup
├── LICENSE                       # Project license file
├── .gitignore                    # Git ignore file
└── README.md                     # Documentation
```

## Supabase Integration

This project connects to Supabase using a publishable key in `supabase.js` and interacts with the `registrations` table.

### Schema Requirements:
**Table Name**: `registrations`

| Column | Type | Description |
|---|---|---|
| `id` | int8 (Identity) | Unique row serial ID |
| `full_name` | text | Attendee's full name |
| `email` | text | Unique email address |
| `contact` | text | Telephone number |
| `branch` | text | College college/branch |
| `academic_year` | text | Year of study |
| `ticket_id` | text | Unique alphanumeric registration code |
| `created_at` | timestamptz | ISO Timestamp of creation |

## Local Setup

1. Clone this repository to your local machine.
2. In the root directory, serve the static files using a local development server. For example:
   ```bash
   npx http-server -p 8080 -c-1
   ```
3. Open [http://localhost:8080](http://localhost:8080) in your browser.

## Deployment Instructions

### GitHub:
1. Initialize git and commit your files:
   ```bash
   git init
   git add .
   git commit -m "Initialize Silent Disco Portal"
   ```
2. Create a repository on GitHub, add it as a remote, and push:
   ```bash
   git remote add origin https://github.com/yourusername/silent-disco.git
   git branch -M main
   git push -u origin main
   ```

### Vercel Deployment:
1. Log in to your Vercel Dashboard.
2. Click **Add New** -> **Project**.
3. Import your GitHub repository.
4. Keep the default settings (No Build Command required, Static directory build is configured out-of-the-box).
5. Click **Deploy**. Vercel will build and host your static files within seconds.
