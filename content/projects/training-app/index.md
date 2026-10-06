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


### Week 6 – REST API, Javalin & Documentation

I uge 6 arbejdede vi med at gøre funktionerne i vores **Training App** tilgængelige gennem et REST API. Vi brugte **Javalin** til at oprette endpoints og koblede dem sammen med vores eksisterende DAO-lag, entities og AI Coach.

#### Det har vi arbejdet med

- Tilføjet Javalin og oprettet `Application` som startpunkt for REST API'et
- Oprettet controllers og routes til:
  - Users
  - Exercises
  - Workout Programs
  - AI Coach
- Implementeret `GET`, `POST`, `PUT` og `DELETE` endpoints til øvelser
- Tilføjet endpoints til at oprette og hente brugere
- Oprettet et endpoint hvor brugeren kan sende spørgsmål til vores AI Coach
- Tilføjet funktionalitet til at generere et træningsprogram ud fra brugerens oplysninger
- Brugt request- og response-DTO'er, så API'et ikke eksponerer vores entities direkte
- Tilføjet validering af blandt andet navne, IDs, antal sæt og træningsdage
- Arbejdet med HTTP statuskoder som `200`, `201`, `204`, `400`, `404` og `405`
- Tilføjet logging af requests
- Samlet fejlbeskeder i et fælles JSON-format med `status` og `msg`
- Oprettet en `requests.http` fil til manuel test af endpoints i IntelliJ
- Dokumenteret endpoints, JSON-formater og statuskoder i projektets README

#### Resultat

Ved slutningen af uge 6 har Training App fået et fungerende **REST API**, som forbinder HTTP requests med projektets eksisterende backend.

Routes og controllers er opdelt efter ansvar, mens DTO'er styrer hvilke data API'et modtager og returnerer. Vi har samtidig tilføjet validering, logging og ensartet fejlhåndtering.

API'et er nu dokumenteret og klar til, at vi kan bygge videre med automatiserede endpoint-tests i næste del af projektet.


### Week 7 – REST Assured, Testcontainers & Integration Tests

I uge 7 arbejdede vi med automatiserede tests af vores **Training App**. Vi byggede videre på vores eksisterende DAO-tests og tilføjede tests af REST API'et med **REST Assured** og **Hamcrest**.

Fokus i denne uge var at teste applikationen med kendte data i en separat testdatabase og sikre, at både gyldige requests og almindelige fejlscenarier bliver håndteret korrekt.

#### Det har vi arbejdet med

- Tilføjet REST Assured til endpoint-tests
- Brugt Hamcrest til at kontrollere statuskoder og JSON-responses
- Oprettet en separat `HibernateTestConfig` med PostgreSQL og Testcontainers
- Ladet DAO implementations modtage en `EntityManagerFactory`, så de kan bruge testdatabasen
- Oprettet kendte brugere, øvelser og træningsprogrammer før tests
- Testet CRUD-funktionalitet, JPQL queries og relationer i DAO-laget
- Tilpasset `Application`, så Javalin kan startes og stoppes under endpoint-tests
- Testet REST endpoints med både gyldige og ugyldige requests
- Testet cases hvor data ikke findes
- Brugt en testversion af AI Coach under endpoint-tests
- Testet `AiCoachService` med lokale JSON-responses fra en Javalin-server, der efterligner Gemini
- Tilføjet `WorkoutProgramService`, som validerer AI-data og gemmer øvelser, træningsprogram og brugerrelation i én transaktion
- Testet rollback, så en fejl under gemning ikke overskriver brugerens eksisterende træningsprogram
- Opdateret API-dokumentationen i README med nye fejlbeskeder og statuskoder

#### Resultat

Ved slutningen af uge 7 har Training App fået en mere komplet testopsætning, som dækker DAO-laget, REST API'et og håndteringen af AI-responses.

Database-tests kører mod en separat testdatabase med kendte data, og AI-tests bruger lokale mock-responses, så testkørslen ikke er afhængig af Gemini API'et.

Den samlede testkørsel gennemførte **36 tests uden fejl**, hvilket giver os større sikkerhed for, at både database-, API- og service-laget fungerer som forventet.
