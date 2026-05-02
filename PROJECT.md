# Glazer Safe and Lock — Website Project

## Project Overview

**Business:** Glazer Safe and Lock  
**Location:** West Sacramento, CA  
**Service Area:** Sacramento and surrounding cities  
**Phone:** (916) 996-9492  
**Hours:** Monday–Friday 9 AM – 4 PM (emergency service available)  
**Colors:** Deep Navy (#0f172a), Gold (#c8962e), Steel Blue (#1e3a5f)

A professional, SEO-optimized single-page website for a locksmith and safe specialist, featuring a fully self-contained floating chatbot widget for FAQs, pricing, booking, image uploads, and blog integration. The site, chatbot, and blog architecture are complete and working as of May 2, 2026.

---

## File Structure

All files reside in the `glazer-safelock/` directory.

```
glazer-safelock/
├── index.html              # Main single-page website (~51KB, ~700 lines)
├── blog.html               # Blog listing page (dynamic content loading)
├── blog-config.json        # Toggle/control file for homepage blog previews
├── posts-index.json        # Manifest/index of all blog posts
├── chatbot.js              # Standalone chatbot script (extracted reference)
├── faq-data.json           # 17 FAQ Q&A pairs for the chatbot
└── posts/
    ├── 001-dial-safe-lock-instructions.html
    ├── 002-dial-vs-electronic-locks.html
    ├── 003-importance-of-safe-servicing.html
    ├── 004-choose-right-safe.html
    ├── 005-fire-ratings-for-secluded-areas.html
    └── 006-safe-opening-methods.html
```

---

## index.html — Main Website

A single-page responsive website with the following sections:

### Navigation Bar
Sticky top navbar with links to: Services, About, Why Us, Pricing, Blog, Service Area, Reviews, Phone CTA.

### Hero Section
Full-width hero with headline tagline, subtitle, phone button, and scroll-down indicator.

### Services Section
Grid of service cards:
- Safe Opening and Repair
- Combination Lock Changes
- Lock Replacement and Upgrades
- Emergency Safe and Lock Service

### About Section
Company background, experience, and trust signals with credentials.

### Why Us Section
Differentiators: Licensed & Insured, Family-Owned, Fast Response, Transparent Pricing.

### Pricing Section
Base rates:
- Service/Trip Fee — $75+
- Safe Combination Change — $175
- Safe Opening & Repair — $275+
- Lock Replacement & Upgrades — $275+ parts

### Service Area
Map and list of cities served.

### Emergency Banner
Prominent emergency call-to-action section.

### Testimonials / Reviews
Fixed reviews from satisfied customers.

### Contact Section
Phone, email, service area reference.

### Footer
Copyright, location, phone.

---

## Chatbot Widget (Fully Inlined in index.html)

The chatbot is **completely self-contained** — no external scripts, no API calls, works on `file://` protocol.

### Features
- **Gold button** (bottom-right) toggles the panel open/closed
- **Header** with avatar, bot name ("Glazer Safe & Lock"), status indicator, close button
- **Message area** with scrollable chat history
- **Suggestion chips**: Services, Pricing, Book a Service, Read Blog, Emergency Help
- **Text input** with send button
- **Image upload** button (FileReader-based, no server needed)
- **Typing indicator** animation
- **Mobile responsive** (full-screen on mobile, panel on desktop)

### Intent Routing
The chatbot uses keyword matching (no AI API) to route user questions:

| Intent | Keywords |
|---|---|
| Booking | book, appointment, schedule |
| Pricing | pric, cost, how much, rate, quote, fee |
| Hours/Location | hour, location, address, open, close |
| Emergency | emergency, urgent, locked out, stuck |
| Image Upload | photo, upload, picture, image |
| Blog — Dial Instructions | dial, instruction, sargent, lagard, kaba |
| Blog — Dial vs Electronic | dial + electronic, mechanical + digital, which lock |
| Blog — Safe Servicing | maintenance, service==service, prevent, inspect, lubricate |
| Blog — Choosing a Safe | choose, buy, purchase, select, recommend, best safe |
| Blog — Fire Ratings | fire, rating, heat, burn, secluded, garage, outbuilding |
| Blog — Safe Opening Methods | manipulation, non-destructive, bypass, scope, drill, drilling, destroy, burglary, peel, pry, crowbar, torch, crack + safe |
| Blog — General | blog, article, read, tips, guides |
| FAQ Fallback | fuzzy-matches against `faq-data.json` (top 2 results) |
| General Fallback | Phone + link to blog |

### FAQ Data
17 Q&A pairs covering common topics: service area, pricing, emergency hours, combination changes, lock types, safe moving, warranty, lockout, response time, payment methods, commercial services, safe maintenance, door-to-door time, safe drilling, service guarantee.

---

## Blog System

### Architecture
- `blog.html` — listing page that fetches `posts-index.json` and renders cards
- `blog-config.json` — controls whether blog previews show on the homepage
- `posts-index.json` — manifest listing all posts with slug, title, excerpt, date, category, reading_time, featured flag
- Individual HTML files in `posts/` subdirectory

### blog-config.json Fields
- `show_on_homepage`: boolean — show/hide blog section on index.html
- `homepage_max_snippets`: 2 — max number of preview cards on homepage
- `featured_posts`: array of slugs — which posts appear on the homepage

### Blog Post Template
Each post includes:
- Unique `<title>` and `<meta name="description">`
- `<link rel="canonical">` for SEO
- Breadcrumb-style navigation
- Phone CTA section
- Font Awesome icons
- Google Fonts (Inter + Playfair Display)
- Full responsive layout

### Published Posts (6)

| # | Slug | Title | Category | Reading Time |
|---|---|---|---|---|
| 1 | 001-dial-safe-lock-instructions | Dial Safe Lock Instructions by Brand | Safe Locks | 7 min |
| 2 | 002-dial-vs-electronic-locks | Dial Locks vs Electronic Locks | Safe Locks | 8 min |
| 3 | 003-importance-of-safe-servicing | The Importance of Safe Servicing | Maintenance | 7 min |
| 4 | 004-choose-right-safe | How to Choose the Right Safe | Buying Guide | 9 min |
| 5 | 005-fire-ratings-for-secluded-areas | Fire Ratings for Secluded Areas | Fire Safety | 8 min |
| 6 | 006-safe-opening-methods | Safe Opening Methods: Non-Destructive vs Drilling vs Burglary | Safe Opening | 9 min |

---

## SEO Strategy
- Semantic HTML5 structure throughout
- Unique meta title and description per page
- Structured heading hierarchy (h1 → h2 → h3)
- Canonical URLs on all blog posts
- Alt-text-ready image placeholders
- Location keywords: West Sacramento, Sacramento, safe opening Sacramento
- Service keywords: safe opening, lock repair, combination change, safe technician
- Mobile responsive design
- Fast loading (single HTTP request for main page, no external dependencies except Google Fonts and Font Awesome)

---

## State & Known Issues

### Done
- Full website with all sections complete
- Floating chatbot fully inlined and working
- Chatbot intent routing for 6 blog posts
- Suggestion chips including "Read Blog"
- FAQ fuzzy matching
- Image upload via FileReader
- All 6 blog posts written and validated
- Syntax error fixed: missing `}` in respond() function (unbalanced brace from blog routing merge)

### Pending
- User (Master Locksmith + Safe Tech of 43 years + Mechanical Engineer) will review and refine all 6 blog posts with expert corrections
- Chatbot may need additional training/tuning
- Additional SEO refinements after content review
- Potential future: hosting deployment, domain setup, analytics

### Deployment
The site is static HTML/CSS/JS — no server required. Deployable to any static host (Netlify, Vercel, GitHub Pages, or traditional web hosting). All files open directly from the filesystem.

---

*Project generated by OpenClaw AI assistant for Glazer Safe and Lock. May 2, 2026.*
