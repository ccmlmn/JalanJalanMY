# MyTripMY — Landing Page Website

A modern, bold app landing page for MyTripMY — built to support affiliate program applications (Klook, Agoda) and showcase the product professionally.

---

## Reference Style

Inspired by modern app landing pages like Pays_e:
- Dark hero with large headline + phone mockups
- Accent color pops (lime/green) on dark background
- "How it works" numbered steps with visuals
- Feature sections alternating left/right layout
- Bold stats banner
- Testimonials / social proof
- Big punchy CTA footer with Download button

---

## Page Sections

### 1. Navbar
- Logo: **MyTripMY** left
- Links center: Home · Features · How It Works · Screenshots · Contact
- CTA button right: **"Get Early Access"** (accent color)
- Behavior: transparent → solid background on scroll, sticky

---

### 2. Hero
- **Background**: Dark (#0F1C18) with subtle green radial glow
- **Headline** (large, white, bold):
  > "Trip planning,  
  > made effortless."
- **Subtext**: One AI chat. Hotels, tours, itinerary — all sorted.
- **CTA buttons**: `Download App ↗`  &  `See How It Works`
- **Visual**: 2–3 floating phone mockups (chat UI · itinerary screen · map view)
- **Floating badges**: "Powered by Gemini AI" · "Malaysia's #1 Travel AI"

---

### 3. Trusted Integrations Bar
- Muted label: "Booking powered by"
- Pill badges in a horizontal row:
  `Agoda`  `Klook`  `Google Maps`  `Google Calendar`  `Firebase`

---

### 4. How It Works
- **Background**: White / light surface
- **Headline**: "How It Works"
- **Subtext**: From idea to full itinerary in seconds.
- Layout: phone mockup left · 3 numbered steps right

**Steps:**
1. **Tell us your trip** — Type naturally. "5 days in Penang, beaches & food, RM2000 budget."
2. **AI builds your plan** — Hotels, tours, and a full itinerary generated instantly.
3. **Book & go** — Confirm bookings, sync calendar, get smart reminders.

---

### 5. Feature Highlight — Chat (Dark background)
- **Headline**: "One chat. Everything handled."
- **Subtext**: No more juggling 10 apps. MyTripMY searches Agoda, Klook, and Google Maps all at once.
- **Visual right**: Phone showing AI chat with hotel result cards
- **3 mini pills below**: 🏨 Hotel Search · 🎟️ Tour Booking · 🗺️ Route Optimization

---

### 6. Feature Highlight — Itinerary (Light background)
- **Visual left**: Phone showing day-by-day itinerary screen
- **Headline**: "Your itinerary, perfectly timed."
- **Subtext**: Optimized routes, day-by-day schedule, synced to Google Calendar with automatic reminders.
- **CTA**: `Build My Itinerary →`

---

### 7. Feature Highlight — Notifications (Accent green background)
- **Headline**: "Smart alerts so you never miss a deal."
- **Subtext**: Price drops, check-in reminders, weather warnings — all proactive, no manual checking.
- **Visual right**: Stacked notification card mockups:
  - 💰 Price dropped! RM185 → RM155/night
  - 🌧️ Rain on Day 3 — indoor alternatives added
  - ⏰ Check-in in 2 hours · You're 40 min away

---

### 8. Feature Cards Grid
- **Headline**: "Everything a traveler needs"
- 6 cards in a 3×2 grid:

| Icon | Title | Description |
|------|-------|-------------|
| 🤖 | AI Trip Planner | Natural language to full itinerary |
| 🏨 | Hotel Aggregator | Compare Agoda, Traveloka, Booking.com side by side |
| 🎟️ | Tour & Activity Booking | Powered by Klook and GetYourGuide |
| 📅 | Calendar Sync | Auto-sync every booking to Google Calendar |
| 🔔 | Smart Notifications | Price drops, weather alerts, check-in reminders |
| 🗺️ | Offline Maps | Download Malaysia maps, navigate without data |

---

### 9. Stats Banner
- Dark background, 4 large numbers in a horizontal row:

| Number | Label |
|--------|-------|
| 16M+ | International arrivals to Malaysia (2025) |
| 5 | Booking platforms unified in one app |
| <3s | Average AI response time |
| RM2000 | Average trip budget handled |

---

### 10. Testimonials
- **Headline**: "What travelers say"
- 3 quote cards with avatar circle, name, country flag emoji
- Use placeholder quotes for affiliate application

---

### 11. Bold CTA Section
- **Background**: Lime/accent green (#BCEF5A)
- **Big headline**: "Plan your Malaysia trip today."
- **Subtext**: Free to use. No account needed to explore.
- **Button**: `Download App` (dark button)
- **Visual**: Phone mockup on the right

---

### 12. Footer
- Logo left
- Links center: Home · Features · Privacy Policy · Terms of Service
- Copyright right: © 2025 MyTripMY. All rights reserved.
- Social icons: GitHub · LinkedIn · Email

---

## Design Tokens

```
Dark background:    #0F1C18
Light background:   #F7FAF9
Brand green:        #1D9E75
Lime accent:        #BCEF5A   ← CTA buttons, highlights, hover states
Text (dark bg):     #FFFFFF
Text (light bg):    #0F1C18
Text muted:         #6B7F79
Heading font:       Syne or Clash Display (bold, geometric)
Body font:          DM Sans or Plus Jakarta Sans
Card radius:        14px
Pill radius:        100px
```

---

## Phone Mockup Content

Use these as placeholder content inside the phone screen illustrations:

**Screen 1 — Chat UI**
```
User:  "Plan 5-day Penang trip, RM2000, beaches & food"

AI:    "Found 12 hotels, 20 attractions & 3 guides.
        Ready to build your itinerary? ✓"

       ┌─────────────────────────────┐
       │ Berjaya Beach Resort        │
       │ ⭐ 4.2 · RM185/night        │
       │ Free cancellation           │
       └─────────────────────────────┘
```

**Screen 2 — Itinerary View**
```
Day 2 — May 11, Penang
────────────────────────────────
09:00  Penang Hill Cable Car   [Klook]
12:00  Penang Road Hawker Stalls
15:00  Georgetown Walking Tour
19:00  Ah Chew Laksa House
```

**Screen 3 — Notifications**
```
💰 Price dropped!
   Berjaya Resort RM185 → RM155/night

🌧️ Heavy rain Day 3
   Indoor alternatives added to your plan

⏰ Check-in in 2 hours
   You're currently 40 min away
```

---

## File Structure

```
mytripmy-website/
├── index.html              ← Single file, all sections
├── README.md               ← This file
└── assets/
    ├── mockup-chat.png
    ├── mockup-itinerary.png
    └── mockup-notifications.png
```

All CSS and JS goes inside `index.html` — no build tools needed. One file, deploy anywhere.

---

## Deploy to Vercel

1. Push the project folder to a GitHub repo
2. Go to [vercel.com](https://vercel.com) → **Add New Project** → Import the repo
3. Framework preset: **Other** (static HTML, no framework)
4. Click **Deploy** — live in under 60 seconds
5. Your URL: `https://mytripmy.vercel.app`

**Optional custom domain:**
- Buy `mytripmyapp.com` (~RM60/year on Namecheap)
- Add it in Vercel under **Settings → Domains**
- Looks more professional on affiliate forms, but `.vercel.app` works fine too

---

## Contact Placeholders

Find and replace these strings in `index.html` before going live:

```
[YOUR FULL NAME]
[YOUR EMAIL ADDRESS]
[YOUR PHONE NUMBER]
[YOUR ADDRESS LINE 1]
[YOUR CITY, POSTCODE]
[YOUR COUNTRY]
[YOUR WEBSITE URL]        ← paste your Vercel URL here
```

---

## Affiliate Application Notes

When filling in Klook / Agoda affiliate forms, use these answers:

| Field | Answer |
|-------|--------|
| Website URL | Your Vercel URL |
| Platform type | Mobile Application |
| Promotion method | In-app affiliate deep links and booking redirects |
| Target audience | International and domestic tourists in Malaysia |
| Monthly traffic | Start honest — they care more about platform type |
| Content category | Travel planning, hotel and activity booking |

**Apply here (do this in Week 1 — approval takes 1–2 weeks):**
- Klook Affiliate → [affiliate.klook.com](https://affiliate.klook.com)
- Agoda Partner → [partners.agoda.com](https://partners.agoda.com)

---

*MyTripMY · Agentic AI Travel Planner for Malaysia*  
*Final Year Project · Universiti Teknologi PETRONAS*
