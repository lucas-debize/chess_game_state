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

### Beta Testing User Roles

| Role Name | Description | Test Responsibilities |
|-----------|-------------|----------------------|
| User | A regular Elyrii user who interacts with the AI mascot, completes challenges, manages journal entries, accesses wellness features, and customizes their experience | Validate feature functionality, test user workflows end-to-end, report bugs and usability issues, provide feedback on AI response quality and gamification mechanics |

---

## 3. Feature Test Matrix

The following 18 features represent the complete feature set to be validated during beta testing. All features are mapped to success criteria and testing methodologies.

### Feature List

| Feature ID | User Role | Feature Name | Description | Priority |
|------------|-----------|--------------|-------------|----------|
| F1 | User | Login | User authenticates with email and password | Critical |
| F2 | User | OAuth Login | User authenticates via external provider (Google, Apple) | Critical |
| F3 | User | Register | User creates a new account via the application | Critical |
| F4 | User | Chat | User interacts with AI mascot | Critical |
| F5 | User | Journal | User creates and manages journal entries | High |
| F6 | User | Mood Tracking | User logs daily mood | High |
| F7 | User | Quests | User views and accepts quests | High |
| F8 | User | Challenges | User completes daily challenges | High |
| F9 | User | Rewards | User earns and views rewards | Medium |
| F10 | User | Notifications | User receives push notifications | Medium |
| F11 | User | Progress View | User views progression dashboard | Medium |
| F12 | User | Challenge Completion | User completes challenges and earns points | High |
| F13 | User | Meditation | User accesses guided meditation sessions | Medium |
| F14 | User | Customization | User customizes mascot appearance | Low |
| F15 | User | Coach | User accesses coaching features | Medium |
| F16 | User | Settings | User manages application settings | Low |
| F17 | User | Theme Toggle | User switches between dark and light modes | Low |
| F18 | User | Logout | User terminates session | Critical |

### Success Criteria and Testing Results

| Feature ID | Success Criteria | Testing Methodology | Status |
|------------|------------------|---------------------|--------|
| F1 | User successfully logs in with valid credentials | Manual functional testing | Achieved |
| F2 | User successfully logs in via OAuth provider | Manual functional testing | Achieved |
| F3 | User successfully creates account | Manual functional testing | Achieved |
| F4 | AI responses are coherent and contextually appropriate | Manual testing + response quality validation | Achieved |
| F5 | Journal entries are saved and retrievable | Manual functional testing | Achieved |
| F6 | Mood data is logged and displayed correctly | Manual functional testing | Achieved |
| F7 | Quests display correctly and can be accepted | Manual functional testing | Achieved |
| F8 | Challenges load and display without lag | Manual functional testing | Achieved |
| F9 | Rewards are granted correctly | Manual functional testing | Achieved |
| F10 | Notifications are received on time | Manual functional testing | Pending |
| F11 | Progress dashboard displays accurate data | Manual functional testing | Achieved |
| F12 | Challenge completion updates progress and grants rewards | Manual testing (10/10 completions successful) | Achieved |
| F13 | Meditation sessions play without interruption | Audio playback testing | Pending |
| F14 | Customization preferences persist across sessions | Preference persistence testing (15 attempts) | Pending |
| F15 | Coach features are accessible and recommendations are appropriate | Manual functional testing | Achieved |
| F16 | Settings changes persist across the application | Preference validation (20 changes) | Pending |
| F17 | Theme toggle works correctly and persists | Manual testing (10/10 toggles successful) | Achieved |
| F18 | Logout terminates session and invalidates tokens | Session management testing (15/15 successful) | Achieved |

---

## Document Information

| Field | Value |
|-------|-------|
| **Project Name** | Elyrii Beta Test Plan |
| **Document Version** | 1.0 |
| **Date** | January 30, 2026 |
| **Classification** | Internal Beta Testing Documentation |
