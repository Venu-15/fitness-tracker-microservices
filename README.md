\# Fitness Tracker — Microservices App



A Java Spring Boot microservices backend for tracking fitness activities and

generating AI-based recommendations. Originally built while completing a

hands-on Spring Boot microservices course, with my own feature added on top.



\## Architecture

\- \*\*eureka\*\* (8761) — service discovery

\- \*\*configserver\*\* (8888) — centralized config for all services

\- \*\*userservice\*\* (8081) — user profiles, PostgreSQL

\- \*\*activityservice\*\* (8082) — tracks activities (type, duration, calories),

&#x20; MongoDB, publishes events to Kafka

\- \*\*aiservice\*\* (8083) — consumes activity events from Kafka, generates

&#x20; recommendations via Gemini AI, MongoDB

\- \*\*gateway\*\* (8080) — routes external requests, JWT auth via Keycloak

\- \*\*fitness-frontend\*\* — React + Vite UI



\## My additions

\- `GET /api/activities/summary?period=weekly|monthly` in `activityservice` —

&#x20; returns total activities, total duration, total calories burned, and a

&#x20; breakdown by activity type for the selected window.



\## Tech stack

Java 24 · Spring Boot 3.5 · Spring Cloud (Eureka, Config, Gateway) ·

MongoDB · PostgreSQL · Kafka · Keycloak (OAuth2/JWT) · React · Maven



\## Running locally

1\. Start MongoDB, PostgreSQL, and Kafka (Docker is easiest).

2\. Run `eureka`, then `configserver`, then `userservice`, `activityservice`,

&#x20;  `aiservice`, then `gateway` — each with `mvnw spring-boot:run`.

3\. (Optional) Run the frontend: `cd fitness-frontend \&\& npm install \&\& npm run dev`

