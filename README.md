# ✦ Merge.AI

**The all-in-one AI workspace suite** — from waitlist to first day on the job.

Merge.AI is a complete, production-ready web application suite covering the full employee lifecycle: marketing landing page, job listings, candidate application, and new hire onboarding — all in pure HTML/CSS/JS with one React component. No build pipeline. No backend. No dependencies.

---

## What's Inside

| File | Purpose |
|---|---|
| `index.html` | Marketing landing page with waitlist |
| `careers.html` | Job listings with search & filters |
| `JobApplication.html` | Candidate job application form |
| `MergeAI_Onboarding.jsx` | New employee onboarding app (React + Claude AI) |

---

## Pages & Features

### `index.html` — Landing Page

The public-facing home page. Built to convert visitors into waitlist signups.

- Sticky glassmorphism nav with smooth-scroll
- Animated hero — gradient text, pulse badge, starfield background
- Waitlist modal that posts to Google Forms via hidden iframe (no backend needed)
- Live waitlist counter with confetti on submit
- Demo video modal — plug in any YouTube or Vimeo URL
- Features, How It Works, Pricing, Testimonials, and FAQ sections
- FAQ accordion — one open at a time
- Footer modals for Roadmap, Changelog, About, Blog, Contact, Privacy, Terms, and Security
- Scroll reveal animations via IntersectionObserver

---

### `careers.html` — Careers Page

A self-contained job board with real-time filtering.

- 8 pre-populated listings across Engineering, Design, Product, Data & AI, Marketing, and Operations
- Live search plus department and location filters
- Level chips — Senior, Mid, Lead, Staff, Principal
- Job detail modal with full description, responsibilities, and requirements
- Inline application form — name, email, LinkedIn, cover letter, CV upload, referral source
- Submit success state
- Perks and benefits section

---

### `JobApplication.html` — Job Application Form

A polished, standalone candidate application. One long form, zero dependencies.

**Six sections:**
1. **Position** — role selector, work type, location preference, start date
2. **Personal Information** — name, email, phone, LinkedIn, portfolio, GitHub
3. **Experience & Background** — current title, years of experience, education, clickable skill pills
4. **Cover Letter & Motivation** — three open-text fields with live character counters
5. **Documents** — drag-and-drop resume and portfolio upload
6. **Logistics** — salary expectation, work authorization, visa sponsorship, referral name

**Also includes:**
- Live progress bar that tracks required field completion in real time
- Per-field inline validation with clear error messaging
- Success confirmation screen with option to resubmit
- Off-white and burnt orange palette with Playfair Display + Figtree typography

---

### `MergeAI_Onboarding.jsx` — New Employee Onboarding App

An AI-powered onboarding companion for new hires. Built in React, backed by the Claude API.

**Five tabs:**

| Tab | What it does |
|---|---|
| Dashboard | Welcome banner, progress stats, completion bar, employee profile |
| Checklist | Day 1 / Week 1 / Month 1 tasks — click to complete, syncs to dashboard |
| Resources | Eight essential resource cards — Handbook, IT, Benefits, OKR, and more |
| Team | Colleague directory with avatars, roles, and departments |
| Ask Merge | Live Claude-powered AI chat pre-loaded with onboarding context |

Dark editorial theme — deep charcoal, gold accents, Syne + DM Sans typography. All employee and team data lives at the top of the file for easy customization.

---

## Quick Start

```bash
git clone https://github.com/your-username/mergeai.git
cd mergeai
open index.html
```

Every HTML file runs locally with no server. For the React onboarding component, drop `MergeAI_Onboarding.jsx` into any Vite, Create React App, or Next.js project.

To deploy the HTML files, push to any static host — Vercel, Netlify, GitHub Pages, or Cloudflare Pages all work without any configuration.

---

## Configuration

### Waitlist Form

The waitlist submits silently to a Google Form.

1. Create a Google Form with an Email field
2. Find the form's POST URL — `https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse`
3. Get the email field's entry ID (e.g. `entry.273801007`) from the pre-filled URL
4. Update `index.html`:

```html
<form
  action="https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse"
  method="POST"
  target="hidden_iframe"
>
  <input type="email" name="entry.YOUR_ENTRY_ID" />
</form>
```

### Demo Videos

In `index.html`, find the `DEMO_URLS` object and replace `null` with real embed URLs:

```js
const DEMO_URLS = {
  placeholder: "https://www.youtube.com/embed/YOUR_VIDEO_ID",
  ai:          "https://www.youtube.com/embed/YOUR_AI_DEMO_ID",
  collab:      "https://www.youtube.com/embed/YOUR_COLLAB_DEMO_ID",
};
```

### Job Listings

In `careers.html`, edit the `JOBS` array. Each entry follows this shape:

```js
{
  id: 1,
  title: "Staff ML Engineer",
  dept: "Engineering",
  icon: "⚡",
  iconClass: "dept-engineering",
  location: "Remote",           // "Remote" | "Hybrid" | "On-site"
  type: "Full-time",
  salary: "$220,000 – $310,000 + equity",
  level: "Staff",
  posted: "2 days ago",
  badges: [{ cls: "badge-new", label: "New" }],
  isHot: true,
  description: "One sentence summary.",
  responsibilities: ["..."],
  requirements: ["..."]
}
```

The UI re-renders automatically when entries are added, removed, or edited.

### Job Application Form

In `JobApplication.html`:

- **Roles** — update the `<option>` list inside `<select id="role">`
- **Skill pills** — add or remove `<label class="pill">` elements in section 3
- **Required fields** — edit the `required` array in the `<script>` block to control progress tracking and validation
- **Colors** — update CSS variables at the top of the `<style>` block:

```css
:root {
  --accent: #D4500A;   /* primary brand color  */
  --bg:     #F7F5F2;   /* page background      */
  --ink:    #1A1A1A;   /* body text            */
}
```

### Onboarding App

In `MergeAI_Onboarding.jsx`, update the data constants near the top:

```js
const employee = {
  name:       "Alex Rivera",
  role:       "Senior Product Designer",
  department: "Design",
  startDate:  "Feb 24, 2026",
  manager:    "Jordan Kim",
  avatar:     "AR",
};

const checklistItems = [ /* Day 1, Week 1, Month 1 tasks */ ];
const teamMembers    = [ /* colleague directory entries  */ ];
```

Update the AI system prompt inside the `AskMerge` component to reflect your company name, culture, and the employee's actual role.

### Footer Modals

In `index.html`, find the `FOOTER_CONTENT` object to edit the Roadmap, Changelog, About, Blog, Contact, Privacy, Terms, and Security modal content.

---

## Design Tokens

Each file has its own design system expressed as CSS custom properties.

**Landing & Careers**
```css
:root {
  --deep:   #050816;
  --purple: #7b2fff;
  --cyan:   #00e5ff;
  --violet: #a855f7;
  --pink:   #e040fb;
  --teal:   #00bcd4;
  --white:  #f0f4ff;
  --muted:  #8892b0;
}
```

**Job Application**
```css
:root {
  --bg:     #F7F5F2;
  --accent: #D4500A;
  --ink:    #1A1A1A;
}
```

**Onboarding App**
```js
const theme = {
  bg:      "#0A0C10",
  accent:  "#F0A500",
  surface: "#111318",
  border:  "#1E2330",
};
```

**Typography** — Syne (headings) and DM Sans (body) across all files. The job application form also uses Playfair Display and Figtree.

---

## Deploying

**Static HTML files** — push to GitHub and enable Pages under Settings → Pages → `main` branch → `/ (root)`. Live at `https://your-username.github.io/repo-name/`.

**Onboarding React component** — deploy via Vercel or Netlify with a Vite or Next.js project. The raw `.jsx` file cannot be served directly.

---

## License

Copyright © 2026 **Kparkay Alvin Togba**. All rights reserved.
