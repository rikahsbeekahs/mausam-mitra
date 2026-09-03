# Mausam Mitra — System Architecture

## 1. Project Purpose

Mausam Mitra (Vaayu AI) is an AI-powered personalized and conversational interface for the existing Government Mausam ecosystem.

We are **not building a replacement weather platform**.

The goal is to make existing Mausam information and services easier to discover, understand, and access according to the user's needs.

Core focus:

- Personalized homepage
- 8 user personas
- AI avatar / conversational assistant
- Easy navigation to existing Mausam services
- Trusted weather information
- Context-aware assistance

---

## 2. High-Level Architecture

```text
                    USER
                      |
                      v
             AI AVATAR / VAAYU AI
                      |
          +-----------+-----------+
          |                       |
          v                       v
   LANGUAGE SELECTION          PERSONA
          |                       |
          +-----------+-----------+
                      |
                      v
             PERSONALIZED HOME
                      |
                      v
                USER QUERY
                      |
                      v
              INTENT + CONTEXT
                      |
                      v
             SERVICE REGISTRY
                      |
                      v
          EXISTING MAUSAM SERVICE
                      |
          +-----------+-----------+
          |           |           |
       Forecast      AQI       Alerts
          |           |           |
          +-----------+-----------+
                      |
                      v
             TRUSTED DATA / API
                      |
                      v
                VAAYU AI
                      |
                      v
          SIMPLE EXPLANATION /
             NAVIGATION
                      |
                      v
                    USER
```

---

## 3. Core Principle

**AI is not the weather-data source.**

Vaayu AI should never invent weather information.

Its responsibilities are:

1. Understand the user's language.
2. Understand the selected persona.
3. Understand the user's intent.
4. Extract relevant context such as location, date, and time.
5. Identify the correct Mausam service.
6. Navigate the user to that service.
7. Explain verified information in simple language when appropriate.

Actual weather information must come from trusted Mausam services or verified APIs.

---

## 4. Main Components

### 4.1 React Frontend

Responsible for:

- AI avatar interface
- Language selection
- Persona selection
- Personalized homepage
- Chat/text input
- Voice input/output
- Navigation to Mausam services
- Displaying service links/cards
- Basic location and profile context

### 4.2 FastAPI Backend

Responsible for:

- API endpoints
- Request validation
- AI orchestration
- Context management
- Service registry
- Weather/service data retrieval
- Navigation decisions
- Error handling

### 4.3 Gemini/Gemma AI Layer

Responsible for:

- Natural-language understanding
- Intent detection
- Persona-aware interpretation
- Language understanding
- Extracting location/date/time
- Generating simple explanations
- Conversational navigation

AI must not fabricate weather facts.

### 4.4 Service Registry

The service registry maps user intent/persona to an existing Mausam service.

Example:

```text
agriculture + rainfall_forecast
        ->
weather forecast / agriculture weather service
```

```text
health_conscious + air_quality
        ->
AQI / air-quality service
```

```text
traveller + destination_weather
        ->
forecast service
```

The registry should remain simple in the MVP.

### 4.5 Existing Mausam Services

Mausam already provides weather-related services such as:

- Forecast
- AQI
- Alerts
- Maps
- Agriculture-related information
- Cyclone information
- Other meteorological services

Mausam Mitra should improve access to these services rather than recreate them.

---

## 5. Example End-to-End Flow

User:

> "Kal mere khet mein baarish hogi?"

AI extracts:

```json
{
  "language": "Hindi",
  "persona": "agriculture",
  "intent": "rainfall_forecast",
  "location": "current_location",
  "date": "tomorrow"
}
```

Backend checks the service registry.

The registry identifies the relevant forecast/agriculture service.

The user is guided to the correct Mausam service.

If verified weather data is available through an approved backend/API, Vaayu AI may explain that data simply.

---

## 6. Personalization Flow

```text
Open Mausam Mitra
        |
        v
Avatar says "Namaste!"
        |
        v
Language selection
        |
        v
Persona selection
        |
        v
Optional onboarding questions
        |
        v
Personalized homepage
        |
        v
User can ask questions
        |
        v
AI understands request
        |
        v
Relevant Mausam service
```

---

## 7. MVP Technology Direction

| Layer | Technology |
|---|---|
| Frontend | React |
| Backend | Python + FastAPI |
| AI | Gemini/Gemma |
| Voice | Browser Speech Recognition + Speech Synthesis |
| Maps | Leaflet or MapLibre |
| Weather/API testing | Open-Meteo initially |
| Existing Mausam integration | Service/page navigation or verified APIs |

Open-Meteo may be used for prototype testing where direct Mausam integration is not yet available. It must not change the product positioning: Mausam Mitra remains an interface for the existing Mausam ecosystem.

---

## 8. MVP Architecture Rule

Build in this order:

1. AI understands a query.
2. AI produces structured intent/context.
3. Backend validates the intent.
4. Service registry selects the correct Mausam service.
5. Backend retrieves verified data where an approved API is available.
6. Frontend navigates/displays the relevant service.
7. AI explains verified information.
8. Avatar communicates the result.

Do not build advanced avatar technology before this pipeline works.
