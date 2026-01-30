# BETA TEST PLAN – Elyrii

## 1. Project Context

Elyrii is a cross-platform mobile application (iOS & Android) designed to provide emotional support and foster positive habits for young people experiencing social isolation. Built with Flutter, the application combines an AI-powered personal assistant (powered by a fine-tuned Mistral-7B conversational model) with a gamified system of daily objectives, quests, and wellness features.

### Core Objectives

- Deliver coherent, emotionally intelligent AI conversations through a personalized mascot
- Encourage positive behavioral habits via gamification (challenges, objectives, reward systems)
- Provide wellness tools (guided meditation, structured journaling)
- Enable mood tracking and longitudinal well-being progression visualization

### Technical Architecture

The backend operates as a microservices architecture using TypeScript/Hono, with discrete services handling authentication, chat interactions, journaling, quest management, and notifications. Data persistence uses PostgreSQL for relational data and Redis for caching and real-time operations. This architecture supports horizontal scaling and ensures service resilience during high-concurrency testing scenarios.

---

## 2. Beta Testing Scope & User Roles

Beta testing encompasses all primary user interactions with Elyrii. The following role will be validated during this testing phase:

\begin{table}
\begin{tabular}{|l|p{3cm}|p{4cm}|}
\hline
\textbf{Role Name} & \textbf{Description} & \textbf{Test Responsibilities} \\
\hline
User & A regular Elyrii user who interacts with the AI mascot, completes challenges, manages journal entries, accesses wellness features, and customizes their experience & Validate feature functionality, test user workflows end-to-end, report bugs and usability issues, provide feedback on AI response quality and gamification mechanics \\
\hline
\end{tabular}
\caption{Beta Testing User Roles}
\end{table}

---

## 3. Feature Test Matrix

The following 18 features represent the complete feature set to be validated during beta testing. All features are mapped to success criteria and testing methodologies.

\begin{table}
\begin{tabular}{|p{1cm}|p{1.2cm}|p{2cm}|p{3.5cm}|p{1.2cm}|}
\hline
\textbf{Feature ID} & \textbf{User Role} & \textbf{Feature Name} & \textbf{Description} & \textbf{Priority} \\
\hline
F1 & User & Login & User authenticates with email and password & Critical \\
\hline
F2 & User & OAuth Login & User authenticates via external provider (Google, Apple) & Critical \\
\hline
F3 & User & Register & User creates a new account via the application & Critical \\
\hline
F4 & User & Chat with AI & User engages in multi-turn conversations with the AI-powered mascot & Critical \\
\hline
F5 & User & View Dashboard & User accesses personalized dashboard with mood tracking and engagement stats & High \\
\hline
F6 & User & Track Mood & User selects and logs their current emotional state; data persists and influences recommendations & High \\
\hline
F7 & User & View Statistics & User reviews activity history, mood trends, and completion metrics & High \\
\hline
F8 & User & Create Journal Entry & User author a new journal entry with optional media attachments & High \\
\hline
F9 & User & Edit Journal Entry & User modifies existing journal entries & High \\
\hline
F10 & User & Delete Journal Entry & User removes journal entries with confirmation workflow & High \\
\hline
F11 & User & View Challenges & User browses daily challenges and objectives with progress indicators & High \\
\hline
F12 & User & Complete Challenge & User completes a challenge and receives gamified rewards and points & High \\
\hline
F13 & User & Access Meditation & User launches and completes guided meditation sessions & Medium \\
\hline
F14 & User & Customize Mascot & User personalizes mascot appearance and personality parameters & Medium \\
\hline
F15 & User & Access Coach & User accesses coaching features for personal development and habit formation & Medium \\
\hline
F16 & User & Access Settings & User configures app settings (theme, notifications, privacy, account management) & Medium \\
\hline
F17 & User & Dark/Light Mode & User toggles between dark and light theme; preference persists & Medium \\
\hline
F18 & User & Logout & User terminates their session securely & Critical \\
\hline
\end{tabular}
\caption{Feature Test Matrix}
\end{table}

---

## 4. Success Criteria & Testing Methodology

\begin{table}
\begin{tabular}{|p{0.8cm}|p{2.5cm}|p{2cm}|p{2cm}|p{1.5cm}|}
\hline
\textbf{Feature ID} & \textbf{Key Success Criteria} & \textbf{Testing Indicator/Metric} & \textbf{Test Method} & \textbf{Target Result} \\
\hline
F1 & User authenticates successfully without application errors; credentials are validated securely & 20 login attempts across different devices and network conditions; 0 failures attributed to application logic & Manual functional testing; cross-device validation (iOS, Android) & Achieved (20/20) \\
\hline
F2 & User authenticates via OAuth provider without errors; token exchange completes successfully & 10 attempts with $\geq$2 OAuth providers (Google, Apple); 0 failures; proper token storage validated & Manual functional testing; OAuth flow validation; token persistence checks & Achieved (10/10) \\
\hline
F3 & User successfully registers with unique credentials; account is created and verified & 15 registration attempts with valid and invalid data; proper error handling; email verification flow & Manual functional testing; form validation testing; database integrity checks & Achieved (15/15) \\
\hline
F4 & User receives coherent, contextually relevant AI responses; conversation maintains semantic continuity & $\geq$50 messages across $\geq$10 distinct conversations; AI response latency <2s; semantic coherence evaluated by domain experts & Manual conversation testing; response latency monitoring; qualitative evaluation & Achieved \\
\hline
F5 & Dashboard loads with accurate, personalized content; no data mismatches or stale information & 20 dashboard loads; all user data (mood, stats, challenges) displayed correctly; real-time updates functional & Manual functional testing; data consistency validation; performance monitoring & Pending \\
\hline
F6 & User mood selection persists correctly; mood data influences subsequent recommendations and statistics & 30 mood selections across multiple sessions; all entries persisted in database; statistics reflect selections accurately & Manual functional testing; database validation; stat calculation verification & Pending \\
\hline
F7 & Statistics accurately reflect user activities; data updates in real-time as user completes actions & Statistics validated against recorded activities across 15 test sessions; no discrepancies in calculations & Manual testing with activity logging; statistical validation; cross-service data verification & Pending \\
\hline
F8 & User creates journal entries; all entries persist in database with correct metadata (timestamp, user ID) & 20 entries created; 100\% successfully saved; retrieval returns correct data & Manual functional testing; database integrity checks; CRUD operation validation & Achieved (20/20) \\
\hline
F9 & User modifies journal entries; changes persist; original and edited versions tracked correctly & 15 edit operations; all changes persist; version control validated (if implemented) & Manual functional testing; data persistence checks; edit history validation & Achieved (15/15) \\
\hline
F10 & User deletes journal entries; deleted entries are removed and not recoverable (unless soft-delete implemented) & 10 deletion operations; all entries removed from user view; no orphaned data & Manual functional testing; database cleanup validation; cascading delete checks & Achieved (10/10) \\
\hline
F11 & Challenges display correctly with accurate progress indicators; filtering and sorting work as designed & 20 views across different challenge states; all progress indicators accurate; UI loads without lag & Manual functional testing; challenge data validation; progress calculation verification & Achieved \\
\hline
F12 & User completes challenge; progress updates, rewards are granted, points are added to user account & 10 challenge completions; all progress updates persist; reward logic executed correctly & Manual functional testing; reward system validation; points ledger verification & Achieved (10/10) \\
\hline
F13 & Meditation sessions launch successfully; audio plays without interruption; session completion is logged & 10 meditation sessions initiated; 100\% successful playback; completion tracked correctly & Manual functional testing; audio playback testing; session logging validation & Pending \\
\hline
F14 & User customization options persist; mascot appearance reflects user selections across sessions & 15 customization attempts; all preferences saved and displayed consistently & Manual functional testing; preference persistence checks; UI rendering validation & Pending \\
\hline
F15 & Coach features are accessible; coaching interactions are logged; recommendations are contextually appropriate & 10 coaching sessions initiated; features accessible without errors; data logged correctly & Manual functional testing; recommendation engine validation; session logging checks & Achieved \\
\hline
F16 & Settings changes persist; user preferences are applied consistently across the application & 20 setting changes (theme, notifications, account); all persisted; app behavior reflects changes & Manual functional testing; preference persistence validation; cross-feature consistency checks & Pending \\
\hline
F17 & Theme toggle switches between dark and light modes; preference persists across sessions & 10 theme toggles; proper CSS/styling applied; preference stored in database & Manual functional testing; theme application validation; persistence checks & Achieved (10/10) \\
\hline
F18 & User session terminates; tokens are invalidated; user cannot access protected resources post-logout & 15 logout attempts; session tokens invalidated; protected endpoints return 401/403 errors & Manual functional testing; token validation; session management verification & Achieved (15/15) \\
\hline
\end{tabular}
\caption{Success Criteria and Testing Methodology}
\end{table}

---

## Document Information

**Project Name:** Elyrii Beta Test Plan  
**Document Version:** 1.0  
**Date:** January 30, 2026  
**Classification:** Internal Beta Testing Documentation
