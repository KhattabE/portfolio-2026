---
title: "Training App"
date: 2026-08-27
---

# Training App

Et portfolio-projekt hvor vi udvikler en træningsapp gennem semesteret.

## Development Log

### Week 1 – Project Setup, JPA & CRUD

I uge 1 startede vi udviklingen af vores **Training App**. Formålet med appen er at hjælpe brugere med at få et træningsprogram baseret på deres oplysninger, træningsniveau, mål og hvor mange dage om ugen de kan træne.

Fokus i denne uge var at få projektets grundlæggende backend og databaseforbindelse på plads.

#### Det har vi arbejdet med

- Oprettet projektets første JPA entity: `User`
- Tilføjet brugeroplysninger som navn, email, alder, højde, vægt og antal træningsdage
- Oprettet enums til:
  - `ExperienceLevel` – Beginner, Intermediate og Advanced
  - `TrainingGoal` – Muscle Gain, Strength, Weight Loss og General Fitness
- Konfigureret JPA og Hibernate
- Forbundet projektet til en fælles PostgreSQL-database
- Oprettet `UserDAO` og `UserDAOImpl`
- Implementeret CRUD-operationer for brugere:
  - Create
  - Read
  - Update
  - Delete

#### Resultat

Ved slutningen af uge 1 har vi fået den grundlæggende database- og JPA-struktur på plads. `User`-data kan nu håndteres gennem DAO-laget, og projektet er klar til at blive udvidet med nye entities, relationer og funktioner i de kommende uger.