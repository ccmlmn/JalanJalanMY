# JalanJalanMY — Agentic AI Travel Planner for Malaysia

## Complete FYP Brainstorm Document

---

## 1. OVERVIEW

### Problem Statement

Tourists visiting Malaysia must juggle multiple separate booking platforms:

- **Hotels**: Traveloka, Agoda, Booking.com
- **Attractions & Tours**: Klook, GetYourGuide, TripAdvisor
- **Transport**: Grab, AirAsia, RapidKL
- **Food**: Google Maps, local hawker guides
- **Events & Activities**: Individual venue websites

There is no single intelligent platform that:

- Connects all services simultaneously
- Understands user preferences
- Proactively manages entire trips
- Provides real-time notifications
- Handles multi-step bookings automatically

### Solution — JalanJalanMY

An agentic AI mobile application (Android + iOS) that acts as a personal Malaysia travel concierge.

**Core value proposition:**

- User types natural language request: "Plan me a 5-day Penang trip under RM2000"
- AI agent parses intent, searches all platforms in parallel, personalizes recommendations
- System handles booking execution, builds itinerary, syncs to calendar
- Sends smart notifications (price drops, check-in reminders, weather alerts)
- All in one app

### Target Users

- **Foreign tourists** visiting Malaysia (primary)
- **Domestic travelers** exploring new states
- **Backpackers & budget groups**
- **Business travelers** needing quick itinerary planning

### Geographic Scope

- Coverage: All of Malaysia
- Major focus: Kuala Lumpur, Penang, Sabah, Sarawak, Langkawi, Melaka, Johor Bahru

### AI Core Technology

- **Agentic LLM**: Google Gemini API (gemini-2.0-flash) with tool-calling and reasoning
- **Framework**: LangChain / LangGraph for multi-agent orchestration
- **Reasoning model**: Used for complex multi-step booking logic and preference learning

### Key Differentiators vs Competitors

| Competitor                | How JalanJalanMY Wins                                                                                                          |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Traveloka / Klook**     | Single-category platforms. JalanJalanMY is the orchestration layer above them — cross-platform, AI-driven, integrated booking  |
| **Google Travel**         | Google shows info only. JalanJalanMY executes bookings, manages calendar, sends alerts, builds personalized itineraries        |
| **ChatGPT Travel Advice** | ChatGPT provides text advice. JalanJalanMY takes action — actual booking, real prices, live availability, calendar integration |
| **Existing travel apps**  | No existing app combines Malaysia-specific context + agentic AI + unified booking across hotels/attractions/transport          |

### FYP Novelty Angle

**Multi-agent orchestration for real-world booking domain** — a genuine research contribution. This combines:

- Tool-calling with external APIs
- Agent memory (user preferences)
- Malaysia-specific knowledge grounding
- Multi-step task decomposition
- Cross-platform aggregation

No published prior work on this specific combination in academic literature.

---

## 2. CORE FEATURES

### MVP Features (Must Have for FYP)

#### 1. Conversational Trip Planner

- **Chat interface** where user types natural language requests
- **NLU parsing**: Extract trip parameters (location, dates, budget, interests)
- **Example input**: "Plan me a 5-day trip to Penang beach area, check-in Friday, budget RM200/night"
- **AI generates**: Complete itinerary with hotels, attractions, restaurants
- **Multi-turn conversation**: Refine results with follow-ups

#### 2. Unified Hotel Search

- **Aggregates from**: Traveloka, Agoda, Booking.com, local boutique hotels
- **Real-time data**: Live prices, availability, cancellation policies
- **Price comparison**: Shows same hotel across platforms side-by-side
- **Filters**: Star rating, location, amenities, reviews, price range
- **Book via**: Redirect to partner platform or affiliate link

#### 3. Attraction & Tour Booking

- **Integrates with**: Klook, GetYourGuide, Google Places
- **Features**: Tickets, guided tours, experiences, cultural activities
- **AI recommendations**: Based on user interests and available time
- **Filters**: Duration, group size, category (nature, culture, food, adventure)
- **Reviews & ratings**: Aggregated from multiple sources

#### 4. Itinerary Builder & Calendar Sync

- **Auto-generates**: Day-by-day schedule from confirmed bookings
- **Optimization**: Minimizes travel time between locations using Google Maps
- **Suggests**: Meal breaks, rest periods, travel transitions
- **Calendar export**: Syncs to Google Calendar / Apple Calendar
- **Smart reminders**: Check-in alerts, tour start times, flight boarding

#### 5. Smart Notifications

- **Price drop alerts**: "Hotel X dropped 15% — book now?"
- **Check-in reminders**: "Check-in in 2 hours at [hotel]"
- **Weather warnings**: "Heavy rain forecast for Day 3 in Penang"
- **Last-minute deals**: "50% off Petronas Towers tickets nearby"
- **Geolocation triggers**: Alerts based on where user is currently

#### 6. Offline Map & Navigation

- **Cached Malaysia maps**: All states, major cities downloadable
- **Navigation**: Walking routes, driving directions, public transport (RapidKL, Penang Bus)
- **Works completely offline**: No internet needed for maps
- **Pinned itinerary**: Shows day's stops on the map
- **Transport integration**: LRT/MRT route guidance

#### 7. Currency & Budget Tracker

- **Live exchange rates**: MYR conversion for all currencies
- **Trip spending tracker**: Auto-tracks all bookings (hotels, food, attractions)
- **Daily budget alerts**: Warns if spending exceeds daily limit
- **Cost breakdown**: By category (accommodation, food, activities, transport)
- **Refund/cancellation tracking**: Manages refund status for cancelled bookings

#### 8. Multilingual Support

- **Languages**: English, Bahasa Malaysia, Mandarin Chinese, Japanese
- **Geolocation-based**: Auto-detect user language
- **All content**: Chat responses, itinerary descriptions, notifications in user's language
- **Critical for**: Foreign tourists, especially Asian visitors

### Extended Features (Nice to Have / FYP 2)

- **🍜 Food Discovery**: Halal certification filters, hawker stall finder, Michelin-star restaurant integration
- **✈️ Flight Search**: AirAsia / MHFlights integration for domestic Malaysia routes
- **🤝 Group Trip Planner**: Shared itinerary, split cost calculator, voting on activities
- **📸 AR Preview**: Point camera at building to get instant AI info & reviews
- **⭐ Personalization Memory**: AI remembers user preferences across multiple trips
- **🎟️ eWallet Payment**: Touch n Go / GrabPay / TNG EWALLET integration for Malaysian users
- **🚗 Car Rental**: Integration with Hertz, Avis, local Malaysian rental agencies
- **🏥 Travel Insurance**: Quick quote and purchase for trip duration
- **📱 Travel Buddy**: Find travel companions, share expenses with them

---

## 3. SYSTEM ARCHITECTURE

### High-Level Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    MOBILE APP (Flutter)                          │
│  Chat UI | Itinerary View | Map | Hotels | Notifications        │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│           API GATEWAY (FastAPI / AWS API Gateway)                │
│  Authentication | Rate Limiting | Request Routing                │
└──────────────────────────┬──────────────────────────────────────┘
                           │
┌──────────────────────────▼──────────────────────────────────────┐
│        AI ORCHESTRATION LAYER (LangChain / LangGraph)            │
│  Agent Reasoning | Tool-Calling | Memory Management              │
└──────────────────────────┬──────────────────────────────────────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
     ┌────▼─────┐   ┌─────▼────┐   ┌──────▼──────┐
     │ Hotel    │   │Attraction│   │ Itinerary   │
     │ Agent    │   │ Agent    │   │ Agent       │
     └────┬─────┘   └─────┬────┘   └──────┬──────┘
          │                │                │
    ┌─────▼─────────────────▼────────────────▼──────┐
    │     INTEGRATION LAYER (Tool Connectors)        │
    │  Agoda API | Klook API | Google Maps | Weather│
    │  Traveloka | GetYourGuide | Calendar API      │
    └─────┬──────────────────────────────────────────┘
          │
    ┌─────▼────────────────────────────────────────┐
    │     BACKEND SERVICES (FastAPI Microservices)  │
    │  User Management | Trip Storage | Bookings    │
    │  Notification Triggers | Analytics            │
    └─────┬────────────────────────────────────────┘
          │
    ┌─────▼────────────────────────────────────────┐
    │         DATABASE & STORAGE LAYER              │
    │  PostgreSQL (Users/Trips) | Redis (Cache)    │
    │  Pinecone (Vector Memory)                     │
    └────────────────────────────────────────────────┘
```

### Data Flow: Complete Booking Example

**Scenario**: User asks "Book a 3-star hotel in Penang beach area, check-in Friday, budget RM200/night"

#### Step 1: Natural Language Understanding

```
User Input: "Book a 3-star hotel in Penang beach area,
             check-in Friday, budget RM200/night"
    ↓
AI Agent parses intent
    ↓
Extracted parameters:
  - Location: Penang
  - Sub-location: Beach area (Batu Ferringhi, Tanjung Bungah)
  - Star rating: 3-star
  - Check-in: Next Friday
  - Budget: RM200/night max
  - Duration: (default 3 nights, clarify if needed)
```

#### Step 2: Parallel API Calls

```
Hotel Agent calls multiple APIs simultaneously:
  - Agoda API → Returns 20 hotels matching filters
  - Traveloka Scraper → Returns 15 hotels
  - Booking.com API → Returns 18 hotels
  - Deduplication → Identify same hotel across platforms
  - Price comparison → Show lowest price per property
```

#### Step 3: AI Ranking & Personalization

```
Agent retrieves user preference vector from Pinecone:
  - User profile: "Budget traveler, likes local experiences,
                  avoids chain hotels, family-friendly"
  - Past trips: (none yet for new user)

AI scores each hotel using:
  - Relevance to preferences (vector similarity)
  - Review quality & recency
  - Cancellation policy user prefers
  - Distance to attractions user is interested in

Top 5 candidates ranked
```

#### Step 4: Recommendation & Presentation

```
AI presents to user:
  "Top pick: Berjaya Beach Resort Penang
   - RM185/night (RM555 total for 3 nights)
   - ⭐ 4.2 rating, 800+ reviews
   - Free cancellation until noon
   - 5-min walk to Batu Ferringhi Beach
   - Why this pick: Local favorite, great value,
                    matches your beach preference"

   Other options:
   - Golden Sands Resort (RM220/night)
   - Lone Pine Hotel (RM165/night — lowest price)
```

#### Step 5: Booking Confirmation

```
User: "Book the Berjaya one"
    ↓
Booking Agent calls:
  - Agoda Booking API (or affiliate deep link)
  - Captures confirmation number
  - Stores booking in PostgreSQL
  - Returns: Confirmation, receipt, hotel contact
```

#### Step 6: Calendar & Notification Setup

```
Calendar Agent:
  - Adds "Check-in: Berjaya Beach Resort" to Google Calendar
  - Time: Friday 3:00 PM (standard check-in)
  - Location: Address + Google Maps link
  - Note: Booking reference, hotel phone, cancellation policy

Notification Agent:
  - Sets reminder: 2 hours before check-in
  - Monitors for price drops (alert if price falls)
  - Tracks flight/transport to hotel
  - Weather forecast for those dates
```

#### Step 7: Itinerary Integration

```
Once hotel is booked, Itinerary Agent can now:
  - Suggest nearby attractions for Day 1, 2, 3
  - Calculate travel time from hotel to attractions
  - Build optimal route (minimize backtracking)
  - Suggest meal times and hawker recommendations
  - Generate final day-by-day itinerary
```

### Key Architectural Decisions

| Decision              | Rationale                                                                                                         |
| --------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **FastAPI backend**   | Async-native, excellent for AI/LLM workloads, auto-generated API docs, Python ecosystem strong for AI             |
| **LangGraph agents**  | Enables graph-based multi-agent flows, better than simple chains for complex workflows, state management built-in |
| **PostgreSQL**        | ACID guarantees for booking transactions, relational structure fits user/trip/booking data well                   |
| **Redis**             | Fast session caching, conversation history (JSON), rate limiting, distributed locks for concurrent bookings       |
| **Pinecone**          | Vector database for user preference embeddings, enables semantic search of attractions, memory across trips       |
| **Firebase FCM**      | Cross-platform push notifications, free tier generous, integrates easily with Flutter                             |
| **Google Maps API**   | Market-standard maps, excellent offline tile caching, routing algorithms                                          |
| **Google Gemini API** | Fast reasoning for complex multi-step tasks, tool-calling native, free tier with generous quotas                  |

---

## 4. AGENTIC AI DESIGN

### Overview

The app doesn't use a single monolithic LLM. Instead, it uses a **multi-agent framework** where a central orchestrator delegates specialized tasks to sub-agents.

**Why multi-agent?**

- **Separation of concerns**: Each agent is expert in its domain
- **Easier to test**: Can debug hotel agent separately from itinerary agent
- **Reusable tools**: Hotel agent's price-comparison logic is not mixed with calendar logic
- **Scalability**: Easy to add new agents (flight booking, food discovery) without touching others
- **Better context window management**: Agents use focused, relevant tokens

### The 6 Core Agents

#### 1. **Orchestrator Agent** (Master Planner)

**Role**: Central command center. Receives user request, understands intent, decides which agents to invoke.

**What it does**:

- Parses natural language into structured goals
- Breaks down complex requests into sub-tasks
- Decides which agents to call and in what order
- Synthesizes final response from sub-agent outputs
- Manages conversation context and memory

**Framework**: ReAct (Reasoning + Acting) via LangGraph
**Tools available**:

- Classify user intent (hotel search, tour guide search, itinerary, notification)
- Invoke specific agents
- Memory retrieval (user preferences, past trips)
- Conversation history management

**Example workflow**:

```
User: "Plan my 5-day Penang trip"
    ↓
Orchestrator parses:
  Intent = TRIP_PLANNING
  Location = Penang
  Duration = 5 days
  ↓
Calls: Hotel Agent → Tour Guide Agent → Attraction Agent → Itinerary Agent
    ↓
Synthesizes results into:
  "Here's your 5-day Penang itinerary: ..."
```

---

#### 2. **Hotel Agent** (Accommodation Specialist)

**Role**: Expert in hotel search, comparison, and booking.

**What it does**:

- Searches hotels by location, budget, amenities
- Compares prices across Agoda, Traveloka, Booking.com
- Filters by star rating, reviews, cancellation policies
- Extracts best value using user preference history
- Handles booking execution

**External tools**:

- Agoda Affiliate API
- Traveloka web scraper (BeautifulSoup)
- Booking.com API
- Google Places API (nearby hotels)
- Review aggregator (Trustpilot, Booking reviews)

---

#### 3. **Tour Guide Agent** (Tour Guide Specialist) — NEW

**Role**: Expert in finding and booking professional tour guides.

**What it does**:

- Searches for licensed tour guides by specialization
- Filters by location, language spoken, availability
- Compares guide ratings, experience, daily rates
- Handles guide booking and confirmation
- Provides guide information (background, credentials, reviews)

**Specializations**:

- Beach tours (Penang, Langkawi, Terengganu)
- Cultural tours (Melaka, Georgetown, Kuching)
- Adventure guides (Sabah climbing, diving, hiking)
- Food tours (hawker guides, street food experiences)
- Nature/eco-tours (rainforest, wildlife viewing)

**External tools**:

- Local Malaysia tour guide databases
- GetYourGuide API (has guide services)
- Klook tour guide/private tour options
- Language filtering (English, Bahasa Malaysia, Mandarin, Japanese)

**Example**:

```
User: "I want a beach tour guide in Penang, English speaker"

Tour Guide Agent:
  → Searches local guide database filtered by:
     location = Penang
     specialization = beaches
     language = English
  → Returns: 5 available guides with profiles, rates (RM150-300/day), reviews
  → User selects guide and books
```

---

#### 4. **Attraction Agent** (Experience Curator)

**Role**: Expert in finding tours, tickets, and experiences.

**What it does**:

- Searches attractions by category (nature, culture, food, adventure)
- Books tours and tickets via Klook, GetYourGuide
- Filters by duration, group size, ratings
- Suggests based on user interests and available time
- Handles pricing and availability

**External tools**:

- Klook API
- GetYourGuide API
- Google Places API
- TripAdvisor scraper
- Weather API (rainy day suggestions)

---

#### 5. **Itinerary Agent** (Schedule Optimizer)

**Role**: Builds optimized day-by-day schedules.

**What it does**:

- Takes confirmed bookings (hotel, tours, guide, attractions)
- Builds logical sequence minimizing travel time
- Suggests meal times and local food spots
- Calculates transport between locations
- Generates day-by-day descriptions
- Exports as calendar events

**External tools**:

- Google Maps API (routing, distance matrix)
- Google Calendar API (event creation)
- Weather API (plan indoor/outdoor by weather)
- Local restaurant DB

---

#### 6. **Notification Agent** (Background Monitor)

**Role**: Continuously watches for events and sends alerts.

**What it does**:

- Sends check-in reminders (2 hours before hotel check-in)
- Sends booking confirmations (hotel, tour guide, attraction booked)
- Sends upcoming event alerts (tour starts in X hours)
- Tracks refund/cancellation status
- Sends tour guide confirmation and meeting point details

**External tools**:

- Firebase Cloud Messaging (FCM)
- Calendar API
- Booking confirmation tracking

---

#### 7. **Conversational Agent** (Chat Interface)

**Role**: Front-facing chat experience. Maintains conversation flow and context.

**What it does**:

- Understands natural language queries
- Maintains multi-turn conversation history
- Clarifies ambiguous requests
- Hands off to specialized agents gracefully
- Provides explanations and alternatives
- Handles casual chat (e.g., "What's a good beach in Penang?")

**Conversation memory**:

- Short-term: Last 20 messages in current session (Redis)
- Medium-term: User preferences from past trips (Pinecone)
- Long-term: Booking history (PostgreSQL)

### Agent Memory Architecture

#### 1. **Short-term Memory (Redis)** — Session-based

- **Duration**: Current conversation session
- **Content**: Last 20 messages, current task state
- **Purpose**: Maintain conversation continuity, context awareness
- **Example**:
  ```json
  {
    "session_id": "user_12345_2024_05",
    "messages": [
      {"role": "user", "content": "Plan Penang trip"},
      {"role": "assistant", "content": "How long..."},
      ...
    ],
    "current_task": "hotel_search",
    "task_state": {
      "location": "Penang",
      "budget": "RM200/night",
      "dates": "June 10-14"
    }
  }
  ```

#### 2. **Long-term User Preference Memory (Pinecone)** — Vector embeddings

- **Duration**: Persistent across trips
- **Content**: User profile vectors, preference embeddings
- **Purpose**: Improve recommendations over time
- **Examples**:
  ```
  User 123 vectors:
  - Budget traveler: 0.92
  - Beach lover: 0.88
  - Foodie: 0.76
  - Avoids crowded spots: 0.81
  - Family-friendly preference: 0.65
  - Halal-friendly: 0.72
  ```

#### 3. **Episodic Memory (PostgreSQL)** — Trip history

- **Duration**: Permanent record
- **Content**: Past trips, hotels visited, attractions seen, bookings
- **Purpose**: Avoid recommending same place twice, learn preferences
- **Example**:
  ```json
  {
    "user_id": 123,
    "past_trips": [
      {
        "destination": "Penang",
        "dates": "May 2024",
        "hotel": "Berjaya Beach Resort",
        "attractions_visited": ["Penang Hill", "Kek Lok Si"],
        "rating_experience": 4.5,
        "notes": "Loved the beaches, too crowded on weekends"
      }
    ]
  }
  ```

### How Agents Collaborate: Example Full Trip Planning

**User**: "Plan my first trip to Malaysia. I have 7 days and RM3000 budget. I love nature and good food."

#### Flow:

1. **Orchestrator Agent** receives request
   - Parses: TRIP_PLANNING, location=Malaysia, duration=7 days, budget=RM3000, interests=[nature, food]
   - Decides agents to invoke: Hotel, Attraction, Itinerary
   - Fetches user profile from Pinecone (first trip, so minimal history)

2. **Hotel Agent** searches in parallel
   - Calls: "Find hotels across Malaysia's best nature spots (Sabah, Penang, Melaka) under RM150/night"
   - Returns: 15 candidates (mix of beach resorts, mountain lodges, city hotels)

3. **Attraction Agent** searches experiences
   - Calls: "Find nature experiences in Sabah (orangutans, hiking), Penang (islands, waterfalls), Melaka (culture)"
   - Returns: Tours for hiking, wildlife, boat trips, local cooking classes

4. **Orchestrator** synthesizes into rough itinerary
   - Day 1-2: Kuala Lumpur (arrival, culture, food)
   - Day 3-4: Penang (beaches, temples, hawker food)
   - Day 5-7: Sabah (wildlife, hiking, local cuisine)

5. **Itinerary Agent** optimizes
   - Calculates flights: KL → Penang → Sabah → KL
   - Minimizes travel days
   - Adds meal recommendations
   - Creates day-by-day schedule

6. **Notification Agent** sets up
   - Price drop monitoring on all 7 hotel nights
   - Flight reminders
   - Tour booking confirmations
   - Weather alerts

7. **Conversational Agent** presents to user
   - Shows 3 itinerary options (budget, mid-range, luxury versions)
   - User picks one
   - Calendar syncs to Google
   - Booking links ready to click

---

## 5. USER INTERFACE SCREENS

### Screen 1: Onboarding / User Profile Setup

**Purpose**: Collect user preferences to personalize recommendations

**Key elements**:

- Profile picture / avatar
- "Where are you from?" — Country selector
- "Budget range?" — Slider (RM500 – RM10,000)
- "What interests you?" — Multi-select buttons (Nature, Culture, Food, Adventure, Shopping, History, Nightlife)
- "Traveling solo or group?" — Radio buttons (Solo, Couple, Small group 3-5, Large group 6+)
- "Travel style?" — Options (Backpacker, Budget, Mid-range, Luxury)
- "Dietary preferences?" — Checkboxes (Halal, Vegetarian, Vegan, Seafood allergies, etc.)
- "Next" button

**Data stored**: User profile vector in Pinecone for personalization

---

### Screen 2: Home / Chat Interface

**Purpose**: Main entry point. Conversational trip planning.

**Layout**:

- **Top bar**: App logo, notification bell, user profile icon
- **Main area**: Chat message history (bubbles - user on right, AI on left)
- **Input area**: Text field + microphone icon + "Send" button
- **Quick suggestions** (below input):
  - "Plan 5-day trip"
  - "Show me hotels in..."
  - "Best attractions today"
  - "What's nearby?"

**Interaction**:

```
User: "Plan a 3-day Penang trip"

Bot: "Great! Let me find options for you...

      📍 Location: Penang
      📅 Duration: 3 days
      💰 Budget: RM2000 (from your profile)
      🎯 Interests: Nature, Food

      I found:
      • 12 hotels matching your criteria
      • 20+ attractions & tours
      • 15 food experiences

      Ready for me to build your itinerary?"

User: "Yes, book the cheapest option for hotels"

Bot: "Perfect! I'm building your itinerary...
      [shows loading animation]
      ✅ Done! Here's your day-by-day plan..."
```

---

### Screen 3: Itinerary View

**Purpose**: Display full trip schedule with all bookings and activities.

**Layout**:

- **Header**: "My Penang Trip" | May 10-14 | ⭐ 4.5 (predicted rating)
- **Cost summary**: RM1,850 spent | RM150 remaining
- **Day tabs**: "Day 1" | "Day 2" | "Day 3" [scrollable]
- **Day details** (for selected day):
  - Morning activity (with time, booking ref)
  - Lunch suggestion
  - Afternoon activity
  - Dinner suggestion
  - Evening activities (optional)
- **Action buttons**: "Add activity" | "Edit" | "Delete" | "Share itinerary"

**Example — Day 2**:

```
🌅 Day 2 — May 11, Penang
  📍 Berjaya Beach Resort

⏰ 8:15 AM
  🚗 Depart to Penang Hill
  Distance: 8 km | Duration: 15 min

⏰ 9:00 AM - 11:30 AM
  🚡 Penang Hill Cable Car & Lookout
  Klook booking #K12345678
  Duration: 2.5 hours
  Booking ref: [Confirm button]

⏰ 12:00 PM
  🍜 Penang Road Hawker Stalls
  Recommended: Char Koay Teow, Popiah
  Google Maps: [Open directions]

⏰ 3:00 PM - Free time
  💡 Suggestions:
    - Georgetown walking tour
    - Beach time at hotel
    - Shopping at Gurney Plaza

⏰ 7:00 PM
  🍛 Dinner: Ah Chew Laksa House
  Book via Google Maps | Price: RM15-20
```

---

### Screen 4: Hotel Search Results

**Purpose**: Show comparison of available hotels.

**Layout**:

- **Filter bar** (collapsible): Price range | Star rating | Amenities | Sort (Price | Rating | Distance)
- **Results list** (card-based):

  ```
  Card 1:
  🏨 Berjaya Beach Resort Penang
  ⭐ 4.2 (843 reviews)
  📍 Batu Ferringhi Beach
  💰 RM185/night | RM555 for 3 nights
  🏷️ Available on Agoda, Traveloka, Booking.com
  ✅ Free cancellation
  🎯 Best value (AI recommended)

  [Buttons: View details | Book]
  ```

- **Detailed view** (on card tap):
  - Photos (carousel)
  - Amenities checklist
  - Room types available
  - Reviews summary
  - Cancellation policy
  - "Book on: [Agoda | Traveloka | Booking.com]" (deep links)

---

### Screen 5: Map View

**Purpose**: Visualize trip geographically.

**Features**:

- **Map canvas**: Google Maps, Malaysia-focused, zoomable
- **Pinned locations**:
  - 📍 Blue: Hotel check-in locations
  - 📍 Red: Attractions & tours
  - 📍 Yellow: Restaurants
  - 📍 Green: Transport hubs (airports, train stations)
- **Routes**: Lines connecting day-to-day movement
- **Info windows**: Tap pin to see activity details, timing, booking status
- **Offline capability**: "Download map for offline use" toggle
- **Bottom sheet**: Current selected day's locations, expandable

**Interaction**:

```
User taps Penang Hill marker
    ↓
Info window shows:
  "Penang Hill
   May 11 | 9:00 AM - 11:30 AM
   Klook booking
   Distance from hotel: 8 km
   [Directions] [Booking details] [Cancel booking]"
```

---

### Screen 6: Notifications Center

**Purpose**: All alerts and reminders in one place.

**Layout**:

- **Filter tabs**: "All" | "Alerts" | "Reminders" | "Deals"
- **Notification list** (reverse chronological):

  ```
  💰 PRICE DROP ALERT
     5 minutes ago
     "Berjaya Beach Resort dropped from RM185 to RM155/night!
      Your booking: RM185. Save RM90 by rebooking.
      Free cancellation available until Friday."
     [Rebook] [Dismiss]

  🌧️ WEATHER WARNING
     2 hours ago
     "Heavy rain forecasted for Penang on May 13.
      We've added indoor activities to your Day 4 itinerary.
      [View changes]"

  ⏰ CHECK-IN REMINDER
     Tomorrow at 2:00 PM
     "Hotel check-in in 2 hours (Berjaya Beach Resort)
      You're currently 40 min away. [Get directions]
      Booking ref: BJ-2024-05-11-001"

  🎉 DEAL ALERT
     1 day ago
     "50% off Petronas Towers tickets!
      Only 3 hours left. Valid for May 12 (your Day 2).
      Current itinerary has Penang Hill. Want to add this?
      [View & add to itinerary]"
  ```

- **Notification settings**: Tap gear icon to mute certain alert types

---

### Screen 7: Budget Tracker

**Purpose**: Real-time spending overview.

**Layout**:

- **Trip summary card**:

  ```
  My Penang Trip
  May 10-14 (3 nights)

  Budget:  RM2,000
  Spent:   RM1,320 (66%)
  Remaining: RM680
  ```

- **Breakdown chart** (pie/bar):
  - 🏨 Accommodation: RM555 (42%)
  - 🎡 Activities & tours: RM420 (32%)
  - 🍜 Food: RM270 (20%)
  - 🚗 Transport: RM75 (6%)

- **Daily breakdown** (swipeable):

  ```
  Day 1 (May 10): RM480 (flights not included yet)
    🏨 Hotel (1 night): RM185
    🍜 Food: RM120
    🎡 Activities: RM175

  Day 2 (May 11): RM415
    🏨 Hotel (1 night): RM185
    🍜 Food: RM140
    🎡 Activities: RM90 (Penang Hill + tour)

  Day 3 (May 12): RM425
    [similar breakdown]
  ```

- **Warnings**:
  - 🔴 "You're at 66% of budget. Slow down?"
  - 🟡 "Food spending is 20% above average for Malaysia"

- **Currency converter**: Quick MYR → User's home currency

---

### Screen 8: Attractions Search / Browse

**Purpose**: Discover activities and book tours.

**Layout**:

- **Category filter**: "All" | "🏞️ Nature" | "🏛️ Culture" | "🍜 Food" | "🏃 Adventure" | "🎭 Nightlife"
- **Results grid** (card-based):

  ```
  Card 1:
  🚡 Penang Hill Cable Car & Viewing Platform
  ⭐ 4.6 (2,341 reviews)
  ⏱️ Duration: 2.5 hours
  💰 From RM45
  Available: Daily 6:30 AM - 10:00 PM
  👥 Good for: All ages, families

  "Visit the highest point in Penang with 360° views.
   Cable car ride + open air & Japanese garden + bistro."

  [View details] [Book via Klook]
  ```

- **Filter sidebar** (collapsible):
  - Duration (1-4 hours, half-day, full-day)
  - Price range
  - Group size
  - Rating (4+ stars, 4.5+ stars)
  - Best for (families, couples, solo, groups)

---

### Screen 9: Settings / Preferences

**Purpose**: Customize app experience and manage account.

**Sections**:

- **Profile**: Name, photo, home country, language
- **Trip Preferences**: Budget default, interests, dietary restrictions, travel style
- **Notifications**:
  - Enable/disable price drop alerts
  - Enable/disable check-in reminders
  - Enable/disable weather alerts
  - Quiet hours (do not notify 10pm-8am)
- **Calendar**: Link Google Calendar / Apple Calendar
- **Currency**: Default display currency (MYR, USD, SGD, etc.)
- **Offline maps**: Download regions for offline use
- **Data & Privacy**: Manage data, export trips, delete account
- **About**: App version, terms, privacy policy, contact support

---

## 6. COST & BUDGET ANALYSIS

### FYP Development Phase (6 months)

#### API Costs

| Service                                  | Details                              | Monthly Cost (FYP)                               | Notes                                        |
| ---------------------------------------- | ------------------------------------ | ------------------------------------------------ | -------------------------------------------- |
| **Google Gemini API (gemini-2.0-flash)** | Free tier (50 req/min) or $2-5/month | Dev/testing: Free tier is generous for FYP scope |
| **Google Maps API**                      | Free tier: 28,500 requests/month     | $0                                               | Covers dev needs; may need upgrade at launch |
| **Google Calendar API**                  | Unlimited at free tier               | $0                                               | No quotas, no costs                          |
| **OpenWeather API**                      | Free tier: 1,000 calls/day           | $0                                               | Sufficient for testing                       |
| **Firebase (FCM)**                       | Free Spark plan                      | $0                                               | Unlimited notifications at free tier         |
| **Firebase Auth**                        | Free tier                            | $0                                               | No payment required                          |
| **PostgreSQL (Supabase)**                | Free tier: 500MB DB                  | $0                                               | Generous for FYP scope                       |
| **Redis (Upstash)**                      | Free tier: 10,000 ops/day            | $0                                               | Sufficient for session/cache during dev      |
| **Pinecone**                             | Free starter: 1 index, 100K vectors  | $0                                               | Enough for learning, small user base         |
| **Backend hosting**                      | Railway/Render free tier             | $0                                               | Can run containerized FastAPI app free       |
| **Klook API**                            | Affiliate program (free)             | $0                                               | Apply for partner access, no dev fee         |
| **Agoda API**                            | Affiliate program (free)             | $0                                               | Apply for partner access, no dev fee         |
| **Traveloka**                            | Web scraper (free, but check ToS)    | $0                                               | Free but legal risk — use only for demo      |

**Total FYP monthly: ~RM0-20 (~$0-5 USD)**

---

#### Non-Cloud Costs

| Item                           | Cost                 | Notes                                                            |
| ------------------------------ | -------------------- | ---------------------------------------------------------------- |
| **App Store Registration**     | One-time $25 USD     | Google Play Developer account (one-time, lifetime)               |
| **Apple Developer Account**    | $99 USD/year         | Required to deploy iOS app                                       |
| **Domain name** (optional)     | $12-15/year          | For API backend; can use free tier subdomain instead             |
| **SSL certificate** (optional) | Free (Let's Encrypt) | Built into most hosting platforms                                |
| **Development tools**          | $0                   | VS Code, Android Studio, Xcode (free), Git (free)                |
| **Anthropic API credits**      | Potentially free     | Anthropic offers research program credits for students/academics |

**Total one-time: ~RM150 (~$25-35 USD)**

---

#### Total FYP Budget Summary

| Category                   | Cost                       |
| -------------------------- | -------------------------- |
| Monthly API usage          | ~RM0-20/month              |
| One-time app store fees    | RM150                      |
| **Total 6-month FYP cost** | **~RM30-80 (~$10-25 USD)** |

**Reality check**: Most will fall within free tiers. You likely need to pay only:

- **Google Play Store registration** ($25 once)
- **Apple Developer account** ($99/year, only if testing on physical iPhone)
- **Gemini API usage** ($0-5/month if exceeding free tier quota)

---

### Post-FYP Production Costs (if launched at scale)

**Assumptions**: 1,000 active users, 10M API calls/month

| Service                      | Monthly Cost | Rationale                                |
| ---------------------------- | ------------ | ---------------------------------------- |
| **Google Gemini API**        | $20-50       | 10M requests/month at scale              |
| **Google Maps API**          | $20-50       | Beyond free tier, pay-as-you-go          |
| **Supabase Pro**             | $25          | 8GB database, real-time support          |
| **Upstash Redis**            | $10-20       | 10M operations/month                     |
| **Pinecone Starter**         | $70          | 1M vectors, storage + retrieval          |
| **Firebase FCM**             | $0           | Still free at 1,000 users                |
| **Backend hosting**          | $20-50       | Railway/Render paid tier, 2-4 containers |
| **Monitoring (Sentry)**      | $0           | Free tier for error tracking             |
| **Email service (SendGrid)** | $0           | Free tier 100 emails/day                 |
| **CDN (optional)**           | $0           | Cloudflare free tier                     |

**Estimated production monthly: $200-400 USD (~RM900-1,800/month)**

**To break even at scale**:

- In-app ads, affiliate commissions from hotel/tour bookings, or premium subscription tier (RM4.99/month for unlimited searches)

---

### Budget Recommendations for FYP

1. **Request Anthropic student credits** (free research program)
2. **Apply for Klook/Agoda affiliate programs immediately** (free, takes 1-2 weeks)
3. **Use only free API tiers** until you need to scale beyond FYP scope
4. **Pay Google Play Store fee** ($25) only if you want to submit to real Play Store (optional for demo)
5. **Avoid Apple Store during FYP** — use Android emulator instead (saves $99)
6. **Use free hosting** (Railway/Render) for backend

**Expected actual spend: RM50-150 for entire FYP project**

---

## 7. TECHNOLOGY STACK

### Frontend / Mobile Layer

#### **Flutter (Dart)**

- **Why chosen**:
  - Single codebase compiles to Android APK + iOS IPA
  - Hot reload for fast iteration (critical for FYP time pressure)
  - Excellent map support via `google_maps_flutter`
  - Strong Firebase integration (auth, FCM notifications)
  - Growing ecosystem, good documentation
  - Dart is modern, fast, and easy to learn

- **Key packages**:

  ```yaml
  flutter:
    sdk: flutter
  google_maps_flutter: ^2.5.0 # Map display & routing
  firebase_auth: ^4.10.0 # User authentication
  firebase_messaging: ^14.8.0 # Push notifications
  google_maps_webservice: ^6.5.0 # Autocomplete, places
  intl: ^0.19.0 # Internationalization (Bahasa, Mandarin, Japanese)
  provider: ^6.0.0 # State management
  http: ^1.1.0 # HTTP requests to backend
  location: ^5.0.1 # GPS, geolocation
  shared_preferences: ^2.2.0 # Local storage
  cached_network_image: ^3.3.0 # Image caching
  table_calendar: ^3.0.0 # Calendar widget for itinerary
  fl_chart: ^0.65.0 # Charts for budget tracking
  ```

- **Platform support**:
  - Android 5.0+ (API level 21+)
  - iOS 11.0+
  - Both use native WebView for embedded browser content

---

#### **Firebase Services**

- **Firebase Auth**:
  - Google Sign-In (for tourists with Google accounts)
  - Email/password registration
  - Anonymous auth (guests browsing without account)
  - Phone OTP (optional, for Malaysia users)

- **Firebase Cloud Messaging (FCM)**:
  - Push notifications for price drops, check-in reminders, weather alerts
  - Cross-platform (works on Android and iOS)
  - Supports data messages + notifications
  - Free tier: unlimited messages

- **Firebase Analytics** (optional):
  - Track user behavior: which features used most, drop-off points
  - Helps understand if AI agent is effective

---

### Backend / API Layer

#### **FastAPI (Python)**

- **Why chosen**:
  - Native async/await — ideal for I/O-heavy operations (API calls, DB queries, LLM calls)
  - Automatic OpenAPI documentation (Swagger UI)
  - Built-in data validation (Pydantic)
  - Python ecosystem strong for AI (LangChain, etc.)
  - Easy to deploy (Docker, Railway, Render)

- **Project structure**:

  ```
  backend/
    ├── main.py                 # FastAPI app initialization
    ├── routes/
    │   ├── auth.py             # Login, registration
    │   ├── trips.py            # Trip CRUD
    │   ├── chat.py             # Conversation endpoint
    │   ├── bookings.py         # Booking management
    │   ├── notifications.py    # Notification triggers
    │   └── integrations.py     # External API calls
    ├── agents/
    │   ├── orchestrator.py      # Master agent
    │   ├── hotel_agent.py       # Hotel search/booking
    │   ├── attraction_agent.py  # Tour search/booking
    │   ├── itinerary_agent.py   # Schedule building
    │   ├── notification_agent.py # Alert triggers
    │   └── conversation_agent.py # Chat interface
    ├── tools/
    │   ├── hotel_search.py      # Agoda, Traveloka, Booking APIs
    │   ├── attraction_search.py  # Klook, GetYourGuide APIs
    │   ├── maps.py              # Google Maps API
    │   ├── calendar.py          # Google Calendar API
    │   ├── weather.py           # OpenWeather API
    │   └── currency.py          # Exchange rates
    ├── models.py                # SQLAlchemy ORM models
    ├── database.py              # DB connection, session
    ├── config.py                # Environment variables
    └── requirements.txt         # Dependencies
  ```

- **Key dependencies**:

  ```
  fastapi==0.104.1
  uvicorn==0.24.0              # ASGI server
  sqlalchemy==2.0.23           # ORM
  pydantic==2.5.0              # Data validation
  python-dotenv==1.0.0         # Environment variables

  # AI & agents
  langchain==0.1.0
  langgraph==0.0.20            # Graph-based agents
  google-generativeai==0.3.0   # Google Gemini API client

  # External APIs
  requests==2.31.0
  aiohttp==3.9.1               # Async HTTP
  google-maps-services==4.10.0
  googlemaps==4.10.0

  # Database
  psycopg2-binary==2.9.0       # PostgreSQL driver
  redis==5.0.0                 # Redis client
  pinecone-client==2.2.3       # Vector DB

  # Utilities
  pyjwt==2.8.0                 # JWT tokens
  python-multipart==0.0.6
  cors==1.0.1
  ```

---

### Database Layer

#### **PostgreSQL (via Supabase)**

- **Why chosen**:
  - ACID transactions essential for booking integrity
  - Relational schema fits user/trip/booking data
  - Supabase provides free tier with 500MB storage
  - Built-in PostGIS extension (if location queries needed)

- **Core tables**:

  ```sql
  users
    - id (UUID primary key)
    - email, password_hash
    - name, country, language
    - profile_data (JSON: interests, budget, travel_style)
    - created_at, updated_at

  trips
    - id (UUID)
    - user_id (FK)
    - destination, start_date, end_date
    - budget, currency
    - status (planning, confirmed, completed, cancelled)
    - created_at, updated_at

  bookings
    - id (UUID)
    - trip_id (FK)
    - booking_type (hotel, attraction, transport)
    - provider (agoda, klook, etc.)
    - booking_ref, booking_date
    - price, currency
    - status (confirmed, cancelled, completed)
    - cancellation_deadline
    - data (JSON: hotel_name, check_in_date, etc.)

  itinerary_items
    - id (UUID)
    - trip_id (FK)
    - day_number, start_time, end_time
    - activity_type, activity_name
    - location_lat, location_lng
    - notes, booking_id (FK, optional)

  user_preferences (for vector DB reference)
    - user_id (FK)
    - preference_vector (reference to Pinecone)
    - last_updated
  ```

---

#### **Redis (via Upstash)**

- **Why chosen**:
  - Fast in-memory caching (conversation history, session state)
  - Pub/Sub for real-time notifications
  - Distributed locks for concurrent booking safety
  - Free tier: 10,000 ops/day (sufficient for FYP)

- **Usage**:
  ```
  Key patterns:
  - session:{session_id}           (conversation state, JSON)
  - user_preferences:{user_id}     (cached preferences)
  - booking_lock:{user_id}         (mutex for concurrent bookings)
  - price_alert:{booking_id}       (price tracking state)
  - notification_queue             (list of pending notifications)
  ```

---

#### **Pinecone (Vector Database)**

- **Why chosen**:
  - Store user preference embeddings (semantic search)
  - Find similar users for collaborative filtering
  - Semantic search of attractions by description
  - Free tier: 1 index, 100K vectors (enough for FYP)

- **Usage**:

  ```
  Index: user_preferences
    - Vector: 384-dim embedding of user preferences
    - Metadata: user_id, interests, budget_range, past_trips

  Index: attraction_embeddings
    - Vector: 384-dim embedding of attraction description
    - Metadata: attraction_id, name, location, rating, price

  Query example:
    "Find attractions similar to user's past preferences"
    → Retrieve user_id=123's vector
    → Query Pinecone for 10 nearest attraction vectors
    → Return top recommendations
  ```

---

### AI & LLM Layer

#### **Google Gemini API (gemini-2.0-flash)**

- **Model**: gemini-2.0-flash
- **Strengths**: Fast reasoning, native tool-calling, free tier with 50 requests/minute
- **Pricing**: Free tier (sufficient for FYP) or $2-5/month if exceeding
- **Usage patterns**:

  ```python
  import google.generativeai as genai

  genai.configure(api_key="YOUR_API_KEY")

  # Create model with tools
  model = genai.GenerativeModel(
      "gemini-2.0-flash",
      tools=[search_hotels, book_hotel, get_reviews]
  )

  # Call with tool use
  response = model.generate_content(
      "Find 3-star hotel in Penang under RM200/night",
      tool_config=tool_config
  )
  ```

**Why Gemini over Claude for this project?**

- Free tier is more generous (50 req/min vs limited tokens for Claude)
- Native tool-calling like Claude
- Fast inference speed
- Less cost risk during development and testing

---

#### **LangChain & LangGraph**

- **Why chosen**:
  - Handles agent orchestration (calling sub-agents in sequence)
  - Memory management (conversation history, user preferences)
  - Tool-calling abstraction (Claude → Agoda API → Claude response)
  - Graph-based workflows (more flexible than simple chains)

- **Agent definition example**:

  ```python
  from langgraph.graph import StateGraph
  from langchain.tools import tool

  # Define tools
  @tool
  def search_hotels(location: str, budget: float) -> str:
      """Search for hotels matching criteria"""
      # Call Agoda/Traveloka APIs
      return json.dumps(results)

  # Create agent with tools
  tools = [search_hotels, book_hotel, get_reviews]

  # Build graph (orchestrator state machine)
  graph = StateGraph(...)
  graph.add_node("orchestrator", orchestrator_agent)
  graph.add_node("hotel_agent", hotel_agent)
  graph.add_node("itinerary_agent", itinerary_agent)
  graph.add_edge("orchestrator", "hotel_agent", condition=...)
  graph.add_edge("hotel_agent", "itinerary_agent", condition=...)
  graph.add_edge("itinerary_agent", "orchestrator")

  compiled = graph.compile()

  # Run workflow
  result = compiled.invoke({
      "user_input": "Plan my trip",
      "user_id": "123"
  })
  ```

---

### Integration / External APIs

#### **Hotel Booking APIs**

| Platform        | API                                  | Cost                             | Status    |
| --------------- | ------------------------------------ | -------------------------------- | --------- |
| **Agoda**       | Affiliate API                        | Free (apply for partner program) | Preferred |
| **Traveloka**   | Official API (limited) / Web scraper | Free / Risky                     | Fallback  |
| **Booking.com** | Affiliate API                        | Free (apply for partner program) | Preferred |

**Integration approach**:

```python
# hotel_search.py
async def search_hotels(location, date_from, date_to, budget):
    # Call Agoda API
    agoda_results = await agoda_search(...)

    # Call Booking.com API
    booking_results = await booking_search(...)

    # Deduplicate & merge
    merged = merge_and_deduplicate(agoda_results, booking_results)

    return merged
```

---

#### **Attraction & Tours**

| Platform              | API           | Cost           | Status       |
| --------------------- | ------------- | -------------- | ------------ |
| **Klook**             | Affiliate API | Free (apply)   | Primary      |
| **GetYourGuide**      | Affiliate API | Free (apply)   | Backup       |
| **Google Places API** | Places API    | $0.007/request | For search   |
| **TripAdvisor**       | Web scraper   | Free (risky)   | Reviews only |

---

#### **Maps & Navigation**

| Service           | API                                  | Cost                       | Notes                            |
| ----------------- | ------------------------------------ | -------------------------- | -------------------------------- |
| **Google Maps**   | Maps SDK, Directions API, Places API | Free tier 28,500 req/month | Offline tiles available          |
| **OpenStreetMap** | Tiles via Leaflet/Mapbox             | Free                       | Alternative if Google hits quota |

---

#### **Calendar**

| Service                 | API                  | Cost | Notes           |
| ----------------------- | -------------------- | ---- | --------------- |
| **Google Calendar API** | Calendar API         | Free | Unlimited calls |
| **Apple CalendarKit**   | Native iOS framework | Free | iOS only        |

---

#### **Weather**

| Service         | API                       | Cost                      | Notes              |
| --------------- | ------------------------- | ------------------------- | ------------------ |
| **OpenWeather** | Current weather, forecast | Free tier 1,000 calls/day | Sufficient for FYP |
| **Weather.com** | Alternative               | Free tier                 | Backup             |

---

#### **Notifications**

| Service                      | Type                | Cost              | Notes               |
| ---------------------------- | ------------------- | ----------------- | ------------------- |
| **Firebase Cloud Messaging** | Push notifications  | Free              | Cross-platform      |
| **SendGrid**                 | Email notifications | Free tier 100/day | For email reminders |

---

### Deployment & Hosting

#### **Backend Hosting**

- **Local dev**: `uvicorn main.py --reload`
- **Production options**:
  - **Railway.app**: Free tier, easy Docker deployment, $5/mo paid tier
  - **Render**: Free tier with auto-sleep, $12/mo for persistent container
  - **Heroku** (legacy): Now paid only

#### **Database**

- **Supabase** (PostgreSQL): Free tier 500MB, paid from $25/mo

#### **Version Control**

- **GitHub**: Free private repos, integrates with Railway/Render for auto-deploy

#### **CI/CD**

- **GitHub Actions**: Free tier, auto-test on push
- **Docker**: Containerize FastAPI app for easy deployment

---

## 8. FYP PROJECT TIMELINE & PLAN

### Semester 1 (FYP 1) — 14 Weeks

#### **Week 1-3: Literature Review & Proposal**

- **Goal**: Establish research foundation and project scope
- **Deliverables**:
  - Literature review report (10-15 pages)
    - Agentic AI frameworks (ReAct, LangGraph, AutoGPT)
    - Tourism app market analysis
    - Multi-agent orchestration papers
    - Malaysia tourism context
  - Problem statement (1-2 pages)
  - Project proposal with objectives and scope (3-5 pages)
- **Milestones**:
  - Week 1: Finalize topic with supervisor
  - Week 2: Complete literature review draft
  - Week 3: Submit proposal to FYP committee

---

#### **Week 4-6: System Design & Architecture**

- **Goal**: Design complete system before coding
- **Deliverables**:
  - System architecture diagram (tech stack visual)
  - Database schema (SQL ER diagram)
  - API endpoint specifications (OpenAPI/Swagger)
  - Agent architecture diagram (how agents interact)
  - UI wireframes for 8+ screens
  - Integration plan for Agoda/Klook/Traveloka
- **Milestones**:
  - Week 4: Finalize tech stack, get supervisor approval
  - Week 5: Complete database and API design reviews
  - Week 6: Finish UI wireframes

---

#### **Week 7-10: Core Backend & AI Agent Development**

- **Goal**: Build working backend with 2-3 functional agents
- **Deliverables**:
  - FastAPI backend with basic CRUD endpoints
  - PostgreSQL + Supabase setup
  - LangGraph orchestrator agent (handles intent parsing)
  - Hotel search agent (integrates 1 API, e.g., Klook)
  - Itinerary builder agent (basic day-by-day scheduling)
  - Claude API integration (tool-calling working)
  - Unit tests for core functions
- **Milestones**:
  - Week 7: FastAPI project structure + DB setup
  - Week 8: LangGraph agents created, Claude API calls working
  - Week 9: Hotel search agent returns results
  - Week 10: Itinerary agent builds valid schedules, test with sample data

- **Checkpoint**: Demo working agent with "Plan me a Penang trip" request returning itinerary

---

#### **Week 11-14: Proposal Defence & Interim Report**

- **Goal**: Present progress to examiners and document findings
- **Deliverables**:
  - Proposal defence presentation (15-20 min, with live demo)
  - Interim report (15-20 pages)
    - System architecture (with diagrams)
    - Agent design and tool definitions
    - Database schema and API endpoints
    - Preliminary results (agent accuracy on sample queries)
    - Challenges encountered and solutions
    - Plan for FYP 2
  - Live demo of working backend
  - Code repository (GitHub with README and setup instructions)
- **Milestones**:
  - Week 11: Complete interim report draft
  - Week 12: Finalize presentation materials
  - Week 13: Conduct proposal defence
  - Week 14: Submit final interim report and code

---

### Semester 2 (FYP 2) — 14 Weeks

#### **Week 1-5: Flutter Mobile App Development**

- **Goal**: Build fully functional mobile UI connected to backend
- **Deliverables**:
  - Flutter project structure (main, routes, models, widgets)
  - Chat UI screen (message bubbles, input field, send button)
  - Itinerary view screen (day-by-day with activity timeline)
  - Hotel search results screen (card-based, filters)
  - Map view screen (Google Maps integration, pinned locations)
  - Notification center screen (alerts, reminders)
  - Budget tracker screen (pie chart, daily breakdown)
  - Settings / profile screen
  - Firebase Auth integration (Google Sign-In, email/pass)
  - Firebase Cloud Messaging setup (receive notifications)
  - HTTP client connected to FastAPI backend
  - Unit & widget tests for key components
- **Milestones**:
  - Week 1: Flutter project setup, basic navigation
  - Week 2: Chat UI + backend connection (text messages flowing)
  - Week 3: Itinerary view + map screen basic layout
  - Week 4: All 8 screens laid out, basic styling
  - Week 5: Full app shell working with placeholder data, Firebase auth tested

---

#### **Week 6-9: Full Integration & All 5 Agents**

- **Goal**: Complete all agents, real booking flows, end-to-end testing
- **Deliverables**:
  - Complete Conversation Agent (chat refinement, multi-turn conversations)
  - Complete Hotel Agent (real Agoda/Traveloka API calls)
  - Complete Attraction Agent (Klook API integration)
  - Complete Itinerary Agent (optimization, Google Calendar sync)
  - Complete Notification Agent (price monitoring, FCM sending)
  - User preference memory (Pinecone vector DB integration)
  - Calendar sync (Google Calendar API, Apple CalendarKit)
  - Multilingual support (English, Bahasa Malaysia, Mandarin, Japanese)
  - Error handling & edge cases
  - Integration tests (full workflows from chat → booking → calendar)
- **Milestones**:
  - Week 6: All agents complete, individually tested
  - Week 7: All APIs connected, real data flowing
  - Week 8: Calendar sync working, notifications sending
  - Week 9: Full end-to-end test: "Plan my Penang trip" → itinerary + calendar + notifications

- **Checkpoint**: Live demo showing complete user journey

---

#### **Week 10-12: User Testing & Evaluation**

- **Goal**: Validate AI recommendations and system usability
- **Deliverables**:
  - User testing plan (10-20 testers, mostly foreign students at UTP)
  - SUS (System Usability Scale) questionnaire
  - Task completion rates (how many users finish a full trip plan)
  - AI recommendation evaluation (accuracy, relevance ratings)
  - Qualitative feedback (interview notes, pain points)
  - Usability issues identified & fixed
  - Performance metrics (response time, API latency)
  - Bug fixes from testing
- **Milestones**:
  - Week 10: Recruit testers, distribute app via TestFlight/Firebase Test Lab
  - Week 11: Collect feedback, analyze results
  - Week 12: Fix critical bugs, finalize app based on feedback

- **Target metrics**:
  - SUS score > 70 (acceptable usability)
  - Task completion rate > 80%
  - AI recommendation accuracy > 75% (users rate recs as helpful)
  - Average response time < 3 seconds

---

#### **Week 13-14: Final Presentation & Dissertation**

- **Goal**: Complete final deliverable and present findings
- **Deliverables**:
  - Final dissertation (40-60 pages)
    - Introduction & motivation (Malaysia tourism, agentic AI gap)
    - Literature review (agentic frameworks, travel recommendation systems)
    - System architecture (detailed with diagrams, algorithms)
    - Implementation details (code snippets, design patterns)
    - Experimental evaluation (user testing results, metrics)
    - Discussion (what worked, what didn't, limitations)
    - Conclusion & future work
    - References
    - Appendix (entity-relationship diagram, API specs, test cases)
  - Final project presentation (20-30 min, with live demo)
  - Working mobile app (APK/IPA, ready to demo on actual devices)
  - GitHub repository (clean code, comprehensive README, setup instructions)
  - Optional: Demo video recorded for online review
  - Optional: Submit to Google Play Store as public app (for real user reach)
- **Milestones**:
  - Week 13: Complete dissertation draft, record demo video
  - Week 14: Final polish, submit all deliverables, conduct final presentation

---

### Key Deliverables Checklist

#### **FYP 1**

- [ ] Literature review report
- [ ] Problem statement & proposal
- [ ] System architecture diagram
- [ ] Database ER diagram
- [ ] API endpoint specifications
- [ ] UI wireframes (8+ screens)
- [ ] Working FastAPI backend
- [ ] 2-3 functional agents (orchestrator, hotel, itinerary)
- [ ] Claude API integration with tool-calling
- [ ] Unit tests
- [ ] Proposal defence presentation + demo
- [ ] Interim report (15-20 pages)

#### **FYP 2**

- [ ] Complete Flutter mobile app (8+ screens)
- [ ] Firebase Auth + Messaging setup
- [ ] All 5 agents complete and integrated
- [ ] All external API integrations (Agoda, Klook, Google Maps, Calendar)
- [ ] User preference memory (Pinecone)
- [ ] Multilingual support (4 languages)
- [ ] Error handling & edge cases
- [ ] Integration tests (end-to-end workflows)
- [ ] User testing with 10-20 testers
- [ ] SUS questionnaire analysis
- [ ] Bug fixes based on user feedback
- [ ] Final dissertation (40-60 pages)
- [ ] Final presentation (20-30 min, with demo)
- [ ] App ready for submission to Play Store/App Store

---

### Research Contribution (for Dissertation)

#### **Novel Contributions**

1. **Multi-Agent Orchestration for Cross-Platform Travel Booking**
   - First published work combining:
     - LangGraph-based agent orchestration
     - Tool-calling across hotel/attraction/itinerary agents
     - Malaysia-specific tourism context
     - Real-time price aggregation from multiple platforms
   - Paper target: IEEE ICICT or Malaysian ICT conference

2. **Evaluation Framework for Agentic AI Travel Planners**
   - Define metrics specifically for travel recommendation AI:
     - Task completion rate (% users complete trip planning)
     - Booking accuracy (% recommendations user books)
     - Itinerary quality (days are well-optimized)
     - Agent tool-call precision (% calls successful)
     - User satisfaction (SUS score, NPS)
   - Contribute to new evaluation benchmarks for this domain

3. **User Preference Elicitation via Multi-Turn Conversation**
   - Method to build user profiles through natural dialogue
   - No explicit forms — AI infers preferences from conversation
   - Measure against baseline (explicit preference forms)

---

### Risk Mitigation

| Risk                                                  | Mitigation                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------------ |
| **API approval delays** (Agoda, Klook take weeks)     | Apply in Week 1; use deep links as fallback in Week 7              |
| **Scope creep** (trying to do too much)               | Lock scope in proposal; cut non-MVP features ruthlessly            |
| **Agent errors** (Claude makes bad recommendations)   | Test heavily with sample data; implement fallback UX               |
| **Flutter platform issues** (iOS/Android difference)  | Test on real devices early; prioritize Android if stuck            |
| **Database performance**                              | Use indexes on trip_id, booking_id; test with 1000+ records        |
| **API rate limits** (hitting Klook/Google Maps quota) | Cache aggressively; implement exponential backoff                  |
| **User testing recruiting** (hard to find testers)    | Start recruiting in Week 6; offer small incentive if budget allows |

---

## SUMMARY

### JalanJalanMY Project Overview

| Aspect                    | Details                                                                                               |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| **App Name**              | JalanJalanMY — Agentic AI Travel Planner for Malaysia                                                 |
| **Target Users**          | Foreign & domestic tourists, backpackers, business travelers                                          |
| **Core Tech**             | Flutter (mobile) + FastAPI (backend) + Claude API (LLM) + LangGraph (agents)                          |
| **Unique Value**          | Multi-agent orchestration across hotel/tour/itinerary platforms                                       |
| **FYP Scope**             | 6 months, MVP features: chat planning, hotel search, itinerary building, calendar sync, notifications |
| **Expected Cost**         | RM50-150 (mostly free tiers)                                                                          |
| **Research Contribution** | Novel multi-agent framework for travel domain; evaluation metrics for agentic AI                      |
| **Success Criteria**      | SUS > 70, task completion > 80%, AI accuracy > 75%, response time < 3s                                |
| **Feasible?**             | Yes, with strict scope management and tight timeline discipline                                       |

---

## APPENDIX: Useful Resources

### Documentation Links

- [LangChain Documentation](https://python.langchain.com/)
- [LangGraph](https://langchain-ai.github.io/langgraph/)
- [Anthropic Claude API](https://docs.anthropic.com/)
- [FastAPI](https://fastapi.tiangolo.com/)
- [Flutter Documentation](https://flutter.dev/docs)
- [Supabase Documentation](https://supabase.com/docs)
- [Firebase Documentation](https://firebase.google.com/docs)

### Example Projects (GitHub)

- Travel recommendation systems (search "travel recommendation github")
- Multi-agent frameworks (LangChain examples)
- Flutter chat apps (search "flutter chat ui")

### Academic Papers

- "ReAct: Synergizing Reasoning and Acting in Language Models" (Yao et al., 2023)
- "Towards Agents as Foundation Models" (Park et al., 2023)
- Multi-agent systems in e-commerce (search ACM, IEEE Xplore)

---

**Document created for FYP brainstorming and NotebookLM conversion**
**Last updated: May 2024**
