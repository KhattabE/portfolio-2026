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


### Week 2 – JPA Relations, JPQL & DAO Tests

I uge 2 byggede vi videre på backend-strukturen i vores **Training App** med fokus på JPA relations, JPQL queries og tests af vores DAO-lag.

#### Det har vi arbejdet med

- Oprettet nye entities:
  - `WorkoutProgram`
  - `Exercise`
- Oprettet `MuscleGroup` enum til kategorisering af øvelser
- Tilføjet JPA relations:
  - `User` → `WorkoutProgram` med `@ManyToOne`
  - `WorkoutProgram` → `Exercise` med `@ManyToMany`
- Holdt relationerne simple og uden unødvendige cascade types
- Oprettet DAO interfaces og implementations til:
  - `WorkoutProgram`
  - `Exercise`
- Udvidet `UserDAO` med nye query-metoder
- Implementeret JPQL queries til blandt andet:
  - Træningsprogrammer efter antal træningsdage
  - Øvelser efter muskelgruppe
  - Brugere efter experience level
  - Brugere efter deres tilknyttede workout program
- Opsat JUnit tests til DAO-laget
- Testet CRUD, JPQL queries og relationen mellem `User` og `WorkoutProgram`

#### Resultat

Ved slutningen af uge 2 har projektet fået en mere sammenhængende databasestruktur, hvor brugere kan forbindes til træningsprogrammer, og træningsprogrammer kan indeholde flere øvelser.

Vi har samtidig implementeret JPQL queries til at hente data på forskellige måder og verificeret DAO-funktionaliteten med automatiserede tests.


### Week 3 – Data Integration & Gemini API

I uge 3 arbejdede vi med **data integration** og integrerede Gemini API i vores **Training App**. Her begyndte vi på en simpel **AI Coach**, som kan sende spørgsmål til Gemini og modtage svar tilbage.

#### Det har vi arbejdet med

- Oprettet en `AiCoachService` til kommunikationen med Gemini API
- Brugt Java `HttpClient` til at sende requests til API'et
- Oprettet DTO'er til request-data
- Brugt Jackson til at konvertere Java-objekter til JSON
- Sendt spørgsmål til Gemini gennem en HTTP `POST` request
- Modtaget JSON-respons fra API'et
- Brugt Jackson til at parse svaret
- Hentet selve AI-svaret ud af JSON-strukturen
- Gemte API-nøglen som en environment variable i stedet for at hardcode den
- Oprettet en test, der bekræfter, at integrationen virker og returnerer et gyldigt svar

#### Resultat

Ved slutningen af uge 3 har projektet fået en fungerende integration til Gemini API. Training App kan nu sende et spørgsmål til vores AI-service, modtage et svar fra Gemini og returnere selve teksten fra svaret.

Integrationen er testet og fungerer som fundament for, at AI Coach-funktionen kan udvides senere i projektet.


### Week 4 – No New Project Integration

I uge 4 arbejdede vi med nye emner på studiet, men der var ikke noget fra ugens undervisning, som gav mening at integrere direkte i vores **Training App** på nuværende tidspunkt.

Vi valgte derfor ikke at tilføje nye features kun for at have noget nyt i projektet. I stedet holdt vi fokus på, at de funktioner vi tilføjer skal være relevante for appens formål og passe ind i den samlede struktur.

#### Resultat

Der blev ikke tilføjet nye funktioner til Training App i uge 4. Projektet står fortsat med den eksisterende JPA-, DAO-, database- og API-integration, og er klar til at blive udvidet igen, når kommende emner passer naturligt ind i projektet.
