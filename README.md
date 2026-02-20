# Merge.AI — Landing Page

> **Everything. Together.** — A production-ready waitlist landing page + careers site for an AI-powered unified workspace product.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CDN-38B2AC?style=flat&logo=tailwind-css&logoColor=white)
![No Build Step](https://img.shields.io/badge/No%20Build%20Step-✓-brightgreen)

---

## 📁 File Structure

```
/
├── index.html       # Main landing page
└── careers.html     # Careers / jobs listing page
```

No dependencies, no build step, no framework. Drop the two files in any static host and it works.

---

## ✨ Features

### `index.html` — Landing Page
- **Sticky glassmorphism nav** with smooth-scroll links
- **Animated hero** with gradient text, pulse badge, and starfield background
- **Waitlist modal** — submits to a Google Form via hidden `<iframe>` (no page redirect, no backend needed)
- **Live waitlist counter** that increments on submission + confetti animation
- **Demo video modal** — swap in your real YouTube/Vimeo embed URL, no other changes required
- **Features, How It Works, Pricing, Testimonials, FAQ** sections — all fully wired
- **FAQ accordion** — one open at a time, smooth CSS transitions
- **Footer modals** for Roadmap, Changelog, About, Blog, Contact, Privacy, Terms, Security
- **Scroll reveal animations** via IntersectionObserver

### `careers.html` — Careers Page
- **8 pre-populated job listings** across Engineering, Design, Product, Data & AI, Marketing, and Operations
- **Live search + department + location filters** with real-time DOM filtering
- **Level chips** (Senior, Mid, Lead, Staff, Principal)
- **Job detail modal** with full description, responsibilities, and requirements
- **Application form** (first name, last name, email, LinkedIn/portfolio, cover letter, CV upload, referral source)
- **Success state** on form submit
- Perks/benefits section

---

## 🚀 Quick Start

1. Clone or download the repo
2. Open `index.html` in a browser — everything works locally with no server

```bash
git clone https://github.com/your-username/mergeai-landing.git
cd mergeai-landing
open index.html
```

For a live URL, deploy to any static host (Vercel, Netlify, GitHub Pages, Cloudflare Pages).

---

## ⚙️ Configuration

### 1. Connect the Waitlist Form

The waitlist submits to a Google Form. To wire it to your own form:

1. Create a Google Form with an **Email** field
2. Get the form's POST URL: `https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse`
3. Get your email field's entry ID (e.g. `entry.273801007`) by inspecting the pre-filled URL
4. In `index.html`, update the `<form>` tag:

```html
<form
  action="https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse"
  method="POST"
  target="hidden_iframe"
  ...
>
  <input type="email" name="entry.YOUR_ENTRY_ID" ... />
</form>
```

### 2. Add Demo Videos

In `index.html`, find the `DEMO_URLS` object in the `<script>` block and replace `null` with your embed URLs:

```js
const DEMO_URLS = {
  placeholder: "https://www.youtube.com/embed/YOUR_VIDEO_ID",
  ai:          "https://www.youtube.com/embed/YOUR_AI_DEMO_ID",
  collab:      "https://www.youtube.com/embed/YOUR_COLLAB_DEMO_ID",
};
```

### 3. Edit Job Listings

In `careers.html`, find the `JOBS` array in the `<script>` block. Each job follows this shape:

```js
{
  id: 1,
  title: "Staff ML Engineer",
  dept: "Engineering",           // matches filter dropdown
  icon: "⚡",
  iconClass: "dept-engineering", // controls icon background color
  location: "Remote",            // "Remote" | "Hybrid" | "On-site"
  type: "Full-time",
  salary: "$220,000 – $310,000 + equity",
  level: "Staff",                // matches level chips
  posted: "2 days ago",
  badges: [{ cls: "badge-new", label: "New" }],
  isHot: true,
  description: "One sentence summary.",
  responsibilities: ["..."],
  requirements: ["..."]
}
```

Add, remove, or edit entries freely — the UI re-renders automatically.

### 4. Update Footer Content

In `index.html`, find the `FOOTER_CONTENT` object to update the Roadmap, Changelog, About, Blog, Contact, Privacy, Terms, and Security modal content.

---

## 🎨 Design Tokens

All colors and styles are defined as CSS custom properties at the top of each file:

```css
:root {
  --deep:   #050816;   /* page background */
  --purple: #7b2fff;   /* primary brand */
  --cyan:   #00e5ff;   /* accent */
  --violet: #a855f7;
  --pink:   #e040fb;
  --teal:   #00bcd4;
  --white:  #f0f4ff;
  --muted:  #8892b0;
}
```

Fonts are loaded from Google Fonts: **Syne** (headings) and **DM Sans** (body).

---

## 🌐 Deploying to GitHub Pages

1. Push both files to the root of your `main` branch
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)` folder
4. Your site will be live at `https://your-username.github.io/repo-name/`

---

## 📄 License

Copyright © 2026 **Kparkay Alvin Togba**. All rights reserved.
