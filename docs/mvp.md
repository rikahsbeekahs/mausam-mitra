# Mausam Mitra — MVP Definition

## 1. MVP Objective

Demonstrate that Mausam Mitra can make the existing Mausam ecosystem easier to access through:

- Personalized homepages
- An AI avatar
- Natural-language interaction
- Persona-aware assistance
- Conversational navigation
- Trusted weather information

We are **not building a replacement weather application**.

---

## 2. Must-Have Features

### A. AI Avatar

A simple animated avatar is enough for the MVP.

It should:

- Greet the user
- Start in Hindi
- Ask the preferred language
- Provide conversational guidance

Advanced avatar APIs are optional.

### B. Language Selection

The user can select their preferred language.

The AI should use the selected language for subsequent interaction.

### C. Persona Selection

The user selects one of the eight SIH personas:

1. Health-conscious
2. Fitness
3. Beachgoers/Surfers
4. Travellers
5. Parents/Families
6. Agriculture/Gardeners
7. Commuters
8. Event Planners

### D. Personalized Homepage

The homepage changes according to the selected persona.

The information is prioritized, not duplicated into a completely new weather platform.

### E. Conversational AI

The user can type or speak a question.

The AI should understand:

- Language
- Persona
- Intent
- Location
- Date
- Time

### F. Service Navigation

The AI maps the request to the appropriate existing Mausam service.

Example:

```text
"Kal mere khet mein baarish hogi?"
        ↓
Agriculture persona
        ↓
Rainfall forecast intent
        ↓
Relevant Mausam forecast/agriculture service
        ↓
Navigate user
```

### G. Trusted Information

The AI must not invent weather data.

When weather data is needed:

```text
Trusted Mausam service / verified API
                ↓
          Actual data
                ↓
           AI explanation
```

---

## 3. MVP Success Demo

The final demo should show:

### Flow 1 — Personalization

```text
Open app
→ Avatar greeting
→ Select language
→ Select Agriculture
→ Agriculture-focused homepage
```

### Flow 2 — AI Navigation

```text
User:
"Kal mere khet mein baarish hogi?"

→ AI understands intent
→ Identifies Agriculture context
→ Selects relevant Mausam service
→ Navigates user
→ User sees trusted forecast information
```

### Flow 3 — Traveller

```text
User selects Traveller
→ Traveller-focused homepage
→ User asks about journey weather
→ AI identifies travel/weather intent
→ AI guides user to relevant forecast information
```

At least two complete persona demonstrations should be polished, while all eight personas must be represented in the prototype.

---

## 4. Simplifications Allowed

Because the prototype has only 15 days:

- Use a simple avatar instead of an advanced digital human.
- Use browser voice APIs initially.
- Use a small service registry instead of a complex recommendation engine.
- Use simple persona configuration instead of ML-based personalization.
- Use existing service/page navigation instead of recreating every Mausam feature.
- Use Open-Meteo for controlled prototype/API testing when necessary, while keeping Mausam as the product ecosystem being enhanced.

---

## 5. Explicitly Out of Scope for MVP

- Building a new weather forecasting model
- Replacing Mausam
- Recreating every Mausam feature
- Training a large custom AI model
- Advanced 3D avatar
- Complex recommendation algorithms
- Full production-scale infrastructure
- Perfect support for every possible user question
- Building a complete independent weather database

---

## 6. MVP Priority

1. Working AI + intent pipeline
2. Service mapping/navigation
3. Personalized homepage
4. All 8 personas represented
5. Trusted data integration
6. Voice interaction
7. Testing
8. UI polish
9. Advanced avatar/features

---

## 7. Definition of Done

The MVP is DONE when:

- [ ] User can open Mausam Mitra.
- [ ] Avatar greets the user.
- [ ] User can select language.
- [ ] User can select one of 8 personas.
- [ ] Homepage changes according to persona.
- [ ] User can ask a weather-related question.
- [ ] AI produces structured intent/context.
- [ ] Backend maps the intent to a Mausam service.
- [ ] Relevant existing service/page can be opened or demonstrated.
- [ ] Weather facts come from a trusted source rather than AI guessing.
- [ ] AI can explain verified information.
- [ ] At least two complete user journeys are demo-ready.
- [ ] All eight personas are represented.
- [ ] Basic failure/clarification cases work.
