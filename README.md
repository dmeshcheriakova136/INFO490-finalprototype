# InterpretAI — Final Prototype

**INFO 490 · Spring 2026 · Daria Meshcheriakova**

A terminology management app for professional medical interpreters. Helps interpreters build, study, and maintain multilingual glossaries before and between live assignments.

**Live demo:** [interpretai.vercel.app](https://interpretai-finalprototype.vercel.app/)

---

## Overview

InterpretAI addresses a real workflow gap: practicing medical interpreters currently juggle handwritten notebooks, Excel files, company PDFs, and scattered web searches with no single integrated place to store and study terminology. This prototype was built and validated through two think-aloud user sessions with professional medical interpreters (May 2026).

---

## Files

| File | Description |
|---|---|
| `index.html` | **Final prototype** — full-featured standalone app. Open directly in any browser, no server needed. |
| `user-testing.html` | **Research platform** — wraps the prototype in a participant task flow with event logging, session export (JSON + CSV), and localStorage persistence. Used for think-aloud sessions. |
| `HW8_ThematicAnalysis.md` | Thematic analysis of two think-aloud interviews. Includes initial codes, themes + evidence table, Outcome/Cause/Solution rubric, and synthesis narrative. |
| `vercel.json` | Deployment config — routes `/` to `user-testing.html`. |

---

## Core Features

### Glossary Management
- Create AI-generated glossaries by describing an upcoming appointment
- Create custom glossaries manually (name, category, language pair)
- Add terms with source + target text, optional photo, and recorded pronunciation
- 4 preset glossaries included: Medical/Orthopedic, Legal/Court, Education/IEP, Business/Negotiation

### AI Glossary Generation
- Keyword-matched terminology packs (9 total): Medical, Legal, IEP/Education, Business, Mental Health, CCHI Exam Prep, NBCMI Exam Prep, General Interpreting, and a General fallback
- Simulates a 1.9-second generation delay with loading state
- *(Production path: replace keyword matching with Claude API or OpenAI GPT-4o call via a backend proxy)*

### Import / Export
- **Import CSV** — two-column file (source term, translation); creates a new glossary automatically
- **Import JSON** — accepts `[{source, target}]` arrays or `{terms: [...]}` objects
- Located under **Create Custom Glossary** screen

### Flashcard Study
- Spaced-repetition style: Again / Hard / Good / Easy ratings stored per term
- Shuffled deck per session
- Shows term image (if attached) and TTS hear button on card reveal
- Session stats: reviewed, correct, accuracy %

### Language Settings
- 52-language selector for source and target language pair
- Saved to `userPrefs` in localStorage; flows through AI generation, term labels, and TTS

### Pronunciation
- **TTS** (Text-to-Speech) on Add Term screen and flashcard reveal — Web Speech API, no dependency
- **Audio recording** — record a pronunciation for any term (MediaRecorder API, stored as base64 WebM, capped at 10s / 500KB)

### Resources & Reference
- **Resources screen** — external links to Multitran, Linguee, Wikipedia Medical Terminology, MedlinePlus, IMIA
- **Prefixes & Suffixes screen** — 45 medical prefixes + 20 suffixes with meanings and examples; searchable with prefix/suffix tab filter

---

## Setup

No build step. No server. No dependencies beyond a Google Fonts CDN call.

```bash
# Clone
git clone https://github.com/dmeshcheriakova136/INFO490-finalprototype.git
cd INFO490-finalprototype

# Open in browser
open index.html         # prototype
open user-testing.html  # research platform
```

To clear saved data between sessions: browser DevTools → Application → Local Storage → delete `interpretai_prototype_v1`.

---

## Database (Supabase)

The prototype is wired to Supabase for persistent cloud storage. To activate:

1. Go to [Supabase Dashboard](https://supabase.com/dashboard/project/clllqdwdphcrhjzcnots) → Project Settings → API → copy the `anon` public key
2. Open `index.html`, find `SUPABASE_ANON_KEY`, and replace the placeholder
3. Run the following SQL in the Supabase SQL Editor:

```sql
create table glossaries (
  id text primary key,
  name text not null,
  category text,
  source_lang text,
  target_lang text,
  icon text,
  source_type text,
  created_at bigint
);

create table terms (
  id text primary key,
  glossary_id text references glossaries(id) on delete cascade,
  source text not null,
  target text,
  added_at bigint,
  image text,
  audio text
);
```

Until the key is set, the app falls back silently to localStorage.

---

## User Testing

Two think-aloud sessions conducted with professional medical interpreters:

| Participant | Experience | Languages | Device |
|---|---|---|---|
| Alona | 13+ years (on-site → remote) | English / Russian / Ukrainian | Windows PC, Edge |
| Astghik | 3 years (medical OPI/VRI) | Russian / Spanish | Laptop (browser) |

**Key findings → changes made:**

| Finding | Fix |
|---|---|
| AI glossary not discoverable — both users went to manual Add Term instead | AI Generate is now the primary CTA on the Create Choice screen |
| "I'm Done" button only in top-right shell corner, outside user attention zone | Button mirrored in the task description panel (user-testing.html) |
| Spanish placeholder blocked non-Spanish interpreters from completing Add Term | Language pair selector added at onboarding; labels update dynamically |
| Users requested external links (Multitran, Lingua, MedLife) | Resources screen added under Profile |
| Users requested prefix/suffix medical terminology reference | Prefixes & Suffixes screen added with 45+ entries |

Full analysis: [`HW8_ThematicAnalysis.md`](./HW8_ThematicAnalysis.md)

---

## Changelog

| Version | Changes |
|---|---|
| v2.0 | Language pair system (52 languages), TTS pronunciation, audio recording, image upload on terms, flashcard image + TTS, Settings screen, Resources screen, Prefixes & Suffixes screen, CSV/JSON import, CCHI/NBCMI/Mental Health AI packs, Supabase integration |
| v1.5 | User-testing harness (`user-testing.html`): 3-task participant flow, event logging, JSON + CSV session export, localStorage persistence, crash recovery |
| v1.0 | Core prototype: Glossary, Study (flashcards), Profile; AI generation (keyword-matched); Add Term; Create Custom Glossary |

---

## Semester Goals — Recap

> *"Build a functional prototype for a terminology management tool that medical interpreters would actually use in their daily workflow."*

- **Research** — Conducted needs-assessment survey and two think-aloud user sessions with practicing medical interpreters. Both confirmed the core problem (fragmented workflows) and validated the core features (flashcards, import/export, notes).
- **Prototype** — Delivered a fully interactive single-file HTML prototype with no build step, deployable to Vercel, runnable offline.
- **User testing** — Built a complete research platform with event logging, session export, and task-completion tracking. Ran two sessions and applied findings back to the prototype.
- **AI integration** — Keyword-matched packs implemented; architecture ready for real LLM API (Claude or GPT-4o) via a backend proxy.
- **Not reached** — Production API key integration and persistent auth/user accounts. These require a backend and are beyond the scope of a course prototype.
