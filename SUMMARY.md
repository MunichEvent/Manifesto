# The Event [Sourcing / Modeling] Manifesto
*(working title, name to be decided)*

> Short version. No jargon. Meant to be read in two minutes.

---

## The problem we keep running into

Most systems only know what is true right now. Ask them what happened last week, or why a piece of data looks the way it does, and there is often no good answer. The history got overwritten the moment something changed. When something goes wrong, nobody can reconstruct how the system actually got there. This gets harder to live with every year, and it is about to get a lot harder, because software itself is starting to make decisions on its own.

---

## Something that already works, and has for a long time

The good news is that a solution to this has existed for a long time, and it works. Instead of only keeping the current state of things, some systems keep a record of everything that happened, and treat the current state as something you calculate from that record, not something you store and quietly overwrite. This idea has been used in production systems for well over a decade. The reason it has stayed niche is not that it fails to deliver, it is that the way it is usually explained keeps it locked inside a small circle of specialists.

---

## What we believe

1. **Design around what happens, not just what is true right now.**
2. **Every decision a system makes should be explainable and reversible.**
3. **Systems should stay resilient under growing and unpredictable pressure.**
4. **Clear boundaries help everyone work safely with a system.**
5. **History is an asset, and it only gets more valuable over time.**

---

## The idea, and the language that gets in the way

### 1. Design around what happens, not just what is true right now

**The idea:** Think of a bank statement instead of a bank balance. A balance only tells you where you stand today. A statement tells you the story of every deposit and withdrawal that got you there, and you can always recalculate the balance from that story. Systems can be designed the same way, around the events that happen, instead of around a single number or record that gets silently changed.

**The language that usually gets in the way:** This is normally introduced as "event sourcing," which sounds like a technical storage detail. In practice it is a different way of thinking about what a system is for.

**Why this matters even more today:** As AI takes on a bigger role in building and running systems, it needs the same thing people need: a clear, honest account of what happened, not just a single number that hides everything behind it.

### 2. Every decision a system makes should be explainable and reversible

**The idea:** It matters to know what a system knew at a given moment, what it decided based on that, and to be able to undo it if the decision turns out to be wrong. A system built around a record of events naturally keeps this information, because the information was never thrown away in the first place.

**The language that usually gets in the way:** People talk about "audit logs" or "event sourcing for traceability," which makes this sound like a compliance checkbox rather than a basic safety requirement.

**Why this matters even more today:** More decisions are now being made by software on its own, through AI agents, rather than by a person clicking a button. When a person is no longer in the loop at the moment of decision, having a trustworthy record of what was known and what was decided stops being a nice extra and becomes essential.

### 3. Systems should stay resilient under growing and unpredictable pressure

**The idea:** Software that reacts to things as they happen, rather than waiting in a strict request and response line, holds up much better under load, and keeps working even when parts of it are under strain.

**The language that usually gets in the way:** This is usually described using terms like "message driven architecture" or "asynchronous systems," which sound like implementation choices rather than a basic requirement for staying online.

**Why this matters even more today:** AI agents do not behave like a handful of people clicking through a website. They can act constantly, in parallel, and at a pace no human team ever could. The kind of pressure that used to be rare is becoming normal.

### 4. Clear boundaries help everyone work safely with a system

**The idea:** A codebase cut into clear, well defined pieces, each responsible for one thing, is easier to understand and safer to change than a codebase where everything is tangled together. When the boundaries are clear, a change made in one place can be trusted not to quietly break something else.

**The language that usually gets in the way:** This idea often gets buried inside academic sounding pattern names, which makes it sound like a rule for architects rather than a practical way to make a codebase easier to work on. It is worth naming the specific technique later, once someone is ready to talk implementation, but the idea stands on its own without it.

**Why this matters even more today:** AI coding assistants are now doing a growing share of the work of writing and changing code. They work far more reliably on a codebase with clear, well defined pieces than on one where everything touches everything else.

### 5. History is an asset, and it only gets more valuable over time

**The idea:** A long, detailed record of what actually happened in a system, over months or years, is worth more than a single snapshot of how things stand today. A system that only keeps today's snapshot has already thrown away most of that value.

**The language that usually gets in the way:** This is often buried inside discussions of "data pipelines" or "event streams," which frame it as infrastructure, when the real point is that the history itself is a source of value.

**Why this matters even more today:** AI is very good at finding patterns in large amounts of data, but it needs context to make sense of what it finds. A rich history of events gives AI exactly that context, and lets it support better decisions, whether those decisions are made by a person or by another AI.

---

## What this looks like in practice

*Optional, one level deeper. To be drafted together, likely a short before and after scenario, described in plain prose. For example, a customer support case where an AI agent makes a decision, and the difference between a system that can explain and undo that decision versus one that cannot.*

---

## Why we wrote this in plain language, on purpose

These ideas have been available for a long time, and they work. If they have not spread further, the problem was never the ideas themselves, it was the language wrapped around them. We wrote this manifesto so that these ideas can be judged on their merits, by anyone, not only by people who already know the vocabulary.

---

## Want to go deeper?

*Links to be added: a short intro article, a talk, a book, a tool. Optional, low friction signing or endorsement can live here too, kept small and secondary.*

---

## Glossary

- **Event sourcing:** a way of building software where every change is stored as an event, and the current state is calculated from that history rather than stored and overwritten directly.
- **Event modeling:** a way of designing a system by first describing the events that happen in it, before deciding how it will be built.
- **CQRS:** short for command query responsibility segregation, a way of separating the part of a system that makes changes from the part that reads data, so each can be built for what it actually needs to do.
- **Message driven:** a way of building software where parts of the system react to messages as they arrive, instead of waiting for each other in a strict sequence.
- **Bounded context:** a clearly defined area of a system with its own rules and its own meaning for the terms it uses, kept separate from other areas to avoid confusion and tangled dependencies.
