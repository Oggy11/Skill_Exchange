# Skill-Exchange (Self-Employment)
> A barter-based Android platform empowering rural communities through skill sharing — no money required.

---

## Overview

**Skill-Exchange** is a community-driven Android application that enables rural artisans and skilled workers — carpenters, electricians, plumbers, mechanics, and more — to exchange services with one another without monetary transactions. Instead of cash, the platform runs on a **Skill Point** economy: one hour of work equals one point. Earn points by helping others, spend them to get help yourself.

Built during an internship at **MindMatrix, Bengaluru**, this project was developed as part of the Android Application Development with Generative AI program under Visvesvaraya Technological University (VTU), 2025–26.

---

## The Problem

In rural communities, skilled workers often face a paradox:

- They have expertise others need
- They need help that others can provide
- But neither party has the cash to pay upfront

The result: jobs go undone, expensive outside technicians are hired, and community cooperation breaks down.

---

## The Solution

Skill-Exchange creates a **digital barter ecosystem** where:

1. Users register their skills and create a profile
2. Anyone can post a service need on the public **Skill Board**
3. Skilled workers propose **swap offers** in response
4. Completed exchanges earn both parties **Skill Points** and grow their **Trust Score**

---

## Key Features

| Feature | Description |
|---|---|
| **Skill Profiles** | Create and manage profiles listing expertise, experience, and availability |
| **Skill Board** | Real-time feed of all open service requests in the community |
| **Need Posts** | Post service requirements with skill category, description, and location |
| **Swap Offers** | Propose barter-based exchanges in response to open posts |
| **Skill Points** | Earn 1 point per hour worked; spend points to request services |
| **Trust Score** | Increases only after both parties confirm a successful exchange |
| **AI Matching** | Generative AI recommends the best barter matches based on skill profiles |
| **AI Assistant** | In-app assistant answers queries and guides users through the platform |
| **Multilingual** | Supports English and Kannada for accessibility |
| **Offline-First** | Core features work without internet via local Room Database |
| **Real-Time Sync** | Firebase Firestore syncs data instantly across devices |

---

## System Architecture

```
┌─────────────────────────────────────────────────────┐
│                   UI Layer (Jetpack Compose)         │
│  Dashboard · Skill Board · Profile · Swap Offers     │
└───────────────────────┬─────────────────────────────┘
                        │
┌───────────────────────▼─────────────────────────────┐
│              Business Logic (ViewModel / MVVM)       │
│   LiveData / StateFlow · Input Validation · Routing  │
└────────┬──────────────────────────┬─────────────────┘
         │                          │
┌────────▼────────┐      ┌──────────▼──────────────────┐
│  Local Storage  │      │      Cloud Services          │
│  Room Database  │◄────►│  Firebase Auth · Firestore   │
│  SharedPrefs    │      │  Real-Time Sync · Notifs     │
└─────────────────┘      └──────────┬──────────────────┘
                                    │
                         ┌──────────▼──────────────────┐
                         │     Generative AI Layer      │
                         │  Skill Matching · Assistant  │
                         └─────────────────────────────┘
```

---

## Database Schema (ERD Summary)

| Entity | Description |
|---|---|
| `USER` | Auth details, location, language preference |
| `SKILL_PROFILE` | User's registered expertise and availability |
| `NEED_POST` | Public service request on the Skill Board |
| `SWAP_OFFER` | Barter proposal responding to a Need Post |
| `SERVICE_EXCHANGE` | Confirmed exchange between two users |
| `SKILL_POINT` | Ledger of points earned and spent per exchange |
| `TRUST_SCORE` | Score updated after mutual confirmation of exchange |
| `NOTIFICATION` | Alerts for offers, confirmations, and status changes |

---

## Tech Stack

| Category | Technology |
|---|---|
| **Language** | Kotlin |
| **IDE** | Android Studio |
| **UI Framework** | Jetpack Compose + View-based UI |
| **Architecture** | MVVM (Model-View-ViewModel) |
| **Local DB** | Room Database (SQLite) |
| **Cloud DB** | Firebase Firestore |
| **Auth** | Firebase Authentication |
| **Background Tasks** | WorkManager |
| **Reactive Data** | LiveData / StateFlow |
| **AI Integration** | Google Generative AI (Gemini) |
| **Version Control** | Git |
| **Min Android** | Android 8.0 (Oreo) API 26+ |

---

## Non-Functional Requirements

- **Usability** — Simple, large-button UI designed for low digital literacy
- **Offline Access** — All core features available without internet
- **Performance** — App launches in under 1 second; instant local data retrieval
- **Security** — Firebase-backed authentication; encrypted user data
- **Scalability** — Cloud infrastructure auto-scales; modular architecture for new features
- **Accessibility** — Kannada language support; minimal text with visual indicators

---

## Development Timeline

| Month | Focus |
|---|---|
| Month 1 | AI Studio prototyping, Android Studio setup, first mini apps, Google Android Developer course |
| Month 2 | Multi-screen apps, Google Cloud Platform (GCP), navigation & user flows |
| Month 3 | Adaptive UI design, Room Database, MVVM with Jetpack Compose |
| Month 4 | Main project wireframing, database integration, AI features, final testing & documentation |

---

## Setup & Installation

### Prerequisites
- Android Studio (latest stable)
- Android SDK (API 26+)
- A Firebase project with Firestore and Authentication enabled
- Google Generative AI API key

### Getting Started

```bash
# Clone the repository
git clone https://github.com/<your-username>/skill-exchange.git
cd skill-exchange
```

1. Open the project in **Android Studio**
2. Add your `google-services.json` from Firebase Console to the `app/` directory
3. Add your Generative AI API key to `local.properties`:
   ```
   GEMINI_API_KEY=your_api_key_here
   ```
4. Sync Gradle and **Run** on a device or emulator (Android 8.0+)

---

## Minimum Hardware Requirements

| Component | Requirement |
|---|---|
| RAM | 2 GB minimum |
| Storage | 100 MB free space |
| OS | Android 8.0 (Oreo) or higher |
| Connectivity | Internet required for auth, sync, and AI features |

---

## Project Structure

```
skill-exchange/
├── app/
│   ├── src/main/
│   │   ├── java/com/skillexchange/
│   │   │   ├── ui/           # Jetpack Compose screens
│   │   │   ├── viewmodel/    # MVVM ViewModels
│   │   │   ├── repository/   # Data layer abstraction
│   │   │   ├── database/     # Room DB entities & DAOs
│   │   │   ├── network/      # Firebase & AI service calls
│   │   │   └── model/        # Data classes
│   │   └── res/
│   │       ├── values/       # strings.xml (EN + KN)
│   │       └── layout/       # XML layouts (legacy views)
│   └── google-services.json  # Firebase config (not committed)
├── local.properties           # API keys (not committed)
└── README.md
```

---

## Internship Details

| Field | Detail |
|---|---|
| **Student** | Arghajeet Gupta (1AM22CD007) |
| **College** | AMC Engineering College, Bangalore |
| **Department** | CSE (Data Science) |
| **University** | Visvesvaraya Technological University, Belagavi |
| **Organisation** | MindMatrix Infotech Pvt. Ltd., Bengaluru |
| **Guide (Internal)** | Dr. Sarojini Y, Prof & HOD, Dept. of CSE(DS) |
| **Guide (External)** | Mr. Tirumal Mutalikdesai, Program Coordinator, MindMatrix |
| **Year** | 2025–2026 |

---

## License

This project was developed as part of an academic internship program. All rights reserved by the author and AMC Engineering College.

---

*Built with Kotlin, Firebase, and Generative AI — for communities that run on trust.*
