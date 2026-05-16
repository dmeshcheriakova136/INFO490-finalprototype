# HW8 — Data Analysis: Think-Aloud Interview Thematic Analysis
**App:** InterpretAI — Terminology Management App for Professional Interpreters
**Participants:** Participant 1 (May 5, 2026) · Participant 2 (May 8, 2026)
**Method:** Thematic analysis following Braun & Clarke (2006); Outcome/Cause/Solution rubric applied to screen capture / event log data

---

## 1. Participants Overview

| | Participant 1 | Participant 2 |
|---|---|---|
| Experience | 13+ years (on-site since 2013, now remote) | 3 years (medical OPI/VRI focus) |
| Languages | English / Russian / Ukrainian | Russian / Spanish (some) |
| Current prep system | Notebooks + PDFs from company + ALTA course materials | Handwritten notebook (keeps nearby) + Excel files on computer |
| Device used | Windows PC, Edge browser | Laptop (browser) |

Both participants are practicing medical interpreters — the exact target user for InterpretAI.

---

## 2. Initial Codes

Working through both transcripts, the following raw codes were identified:

**Terminology management behaviors (pre-interview):**
- Hybrid analog/digital workflows (notebook + Excel + PDF + online search)
- Writing by hand aids memorization; digital search aids recall during live calls
- Company-provided PDFs as reference glossaries
- Expert users rely on experience pattern-matching, not active prep
- Team collaboration as informal knowledge-sharing mechanism
- Consistency is the primary success factor cited by both
- AI is disrupting the field; users are motivated to adapt

**App testing behaviors:**
- Navigated to "quick-add-term" instead of AI generation feature (Task 1 bypass)
- Spontaneously connected Notes section to professional note-taking during calls
- Language default (Spanish) created confusion and blocked real input
- Couldn't locate "I'm Done" button without verbal intervention from researcher
- Import/Export feature discovered organically and immediately validated
- Flashcard study completed successfully and independently
- Task 2 ("Add a term") completed in 1.3 seconds — skipped rather than done
- Both users needed clarification about what the interactive middle screen was

**Post-test feedback:**
- Flashcards validated as a preferred memorization method (Participant 1's favorite)
- Import/Export recognized as solving a real problem (existing PDFs/Excel)
- Feature requests: external links (Multitran, Lingua), resource hub (Wikipedia, MedLife), prefix/suffix breakdowns for medical terminology, certification exam prep content (CCHI, NBCMI)

---

## 3. Themes + Evidence Table

| Theme | Description | Supporting Quotes |
|---|---|---|
| **T1: Fragmented workflows validate the core problem** | Both participants described multi-tool, ad-hoc systems with no single home for terminology. The app addresses a real, felt pain point. | *"Old fashioned writing, you know, in a notebook, or you can look it up. So it's a old variety… sometimes just write it down in the notebook."* — Participant 1 [3:47] |
| **T2: AI feature was not discoverable** | Task 1 was "Create an AI-generated glossary." Participant 1 bypassed the AI feature entirely and went to manual add-term. She completed Task 1 in 15 seconds without using AI. | Event log: Task 1 ended via `reason: "self_reported_without_flag"`, duration 15,506ms. User navigated: `glossary → quick-add-term → add-term → save-term`. |
| **T3: Task navigation UI ("I'm Done" button) was invisible** | Both sessions required the researcher to verbally direct users to the top-right task button. Users were focused on the app screen and the button was outside their visual focus. | *"Top right, where exactly here? Oh, it's on the top right. Blue Button."* — Participant 1 [14:27], after researcher guidance |
| | | Event log: Task 2 (`Add a term`) completed in 1,315ms — Participant 1 clicked "I'm done" as soon as she found the button, without completing the task. |
| **T4: Language placeholder broke the input flow** | Both participants are not Spanish interpreters. The Spanish default placeholder text blocked them from meaningfully completing the add-term task and prevented real data entry. | *"It wouldn't let us save it because we don't know in Spanish."* — Participant 1 [14:49] |
| | | Participant 2 [~09:40]: *"I know it's all Spanish, but it is placeholders for now"* (researcher clarification required) |
| **T5: Core features (flashcards, notes, import/export) were immediately recognized as valuable** | Three features directly mapped onto existing user behaviors and were validated without prompting. No further explanation needed; users "got it" instantly. | *"Oh, so it does import and export like you said. Let's say we have the digital glossary, we can import here and export. That's pretty cool."* — Participant 1 [13:55] |
| | | *"I found this useful to memorize the words and terminology using the flashcards."* — Participant 1 [20:01] |
| **T6: Users want the app connected to their existing ecosystem** | Experienced interpreters already have established external resources. They want InterpretAI to enhance their workflow, not replace it. Integration is expected. | *"Maybe add resources, also link it from Wikipedia or med life… and also suffixes and prefixes."* — Participant 1 [21:10] |

---

## 4. Screen Capture / Event Log: Outcome · Cause · Solution

### Task 1 — Create an AI-generated glossary

| | |
|---|---|
| **Outcome** | NOT achieved as intended. Participant 1 manually added a term instead of using AI generation. Event log shows path: `glossary → quick-add-term → add-term → save-term`. AI generation feature was never invoked. |
| **Cause** | The "Generate AI Glossary" entry point was not visible or distinguishable from the manual add-term flow. The most prominent action (`quick-add-term`) captured her attention first. The task description didn't point toward the AI feature. |
| **Solution** | Make "Generate AI Glossary" the primary, visually dominant CTA on the Glossary screen — larger button, distinct color, placed above the manual option. Consider adding a brief one-liner in the task description ("Use AI to build a glossary from a medical appointment"). |

---

### Task 2 — Add a term

| | |
|---|---|
| **Outcome** | Technically completed (button clicked) but not meaningfully done. Event log: duration = 1,315ms — Participant 1 found the "I'm Done" button and immediately clicked it without adding a real term. |
| **Cause** | Two compounding issues: (1) language confusion from the Spanish default blocked her from entering her own terms; (2) after struggling with Task 1 and the button discovery, she was in "mode-complete" rather than engaged. |
| **Solution** | (1) Show a language-pair selector at onboarding or allow users to set their language pair before entering tasks — removing Spanish as the only default. (2) Consider placing a brief instruction in the task pane ("Add a term in your working language"). |

---

### Task 3 — Study at least 3 flashcards

| | |
|---|---|
| **Outcome** | ACHIEVED. Participant 1 successfully reviewed 3 cards (event log: `task3_threshold_reached`, `reviewed: 3`, duration 34,899ms). She reached the study screen independently and completed the task without intervention. |
| **Cause** | The study/flashcard flow is visually clear and familiar. The "Study from detail" button in the glossary detail view led her directly to the study mode. Flashcards are a format she already uses (favored method from pre-interview). |
| **Solution** | This flow works — preserve it. Expand: Participant 1 suggested adding prefix/suffix cards and certification exam prep content (CCHI/NBCMI). Participant 2's partial session also showed her navigating toward the study flow, confirming its discoverability. |

---

### Shell task navigation ("I'm Done" button)

| | |
|---|---|
| **Outcome** | Required verbal intervention in both sessions. Users did not locate the button without prompting from the researcher. |
| **Cause** | The button lives in the testing shell frame (top-right corner) while users' visual focus stays on the app viewport in the center. The button is outside the natural attention zone during task immersion. |
| **Solution** | Move or mirror the task-completion trigger into the task description panel on the left (below the task text), or add a persistent contextual prompt at the bottom of the app viewport that mirrors the shell's "I'm Done" button state. |

---

## 5. Synthesis Narrative

Both think-aloud sessions converged on a consistent picture: InterpretAI's core value proposition is real and immediately legible to professional interpreters, but two interface issues blocked users from engaging fully with the AI feature and creating friction around task navigation.

Every interpreter interviewed described the same fragmented workflow: a notebook kept nearby, some Excel files on the computer, PDFs from companies, and a scattered set of online searches during live interpreting calls. The problem is real. InterpretAI addresses it directly by offering a unified space for term management, flashcard study, and team notes—all familiar behaviors that users already value. This validation was clear in their immediate recognition of the import/export feature and their enthusiasm for flashcards.

The flashcard study flow (Task 3) was the only task completed successfully and independently by Participant 1, and the event log confirms it: she navigated there herself, reviewed three cards, and hit "I'm done" without hesitation. This flow works because it's visually clear, uses a familiar metaphor, and aligns with how interpreters already study (both participants described using handwritten or digital flashcard methods during pre-interview).

The AI generation feature (Task 1), however, was never actually used. Participant 1 went straight to "quick-add-term," the most visible manual option, and completed the task without touching the AI flow. This suggests that the AI entry point is either not visually prominent or not clearly labeled as distinct from the manual add-term action. The event log shows she completed the entire task in 15 seconds—faster than expected, which indicates she bypassed the intended path rather than explored it.

The "I'm Done" navigation button issue is secondary but creates measurement artifacts: Task 2 was recorded as completed in 1.3 seconds, meaning Participant 1 found the button and immediately pressed it without attempting to add a term. The language default (Spanish) was a contributing factor—she noted that the Spanish placeholder blocked her from entering her own data—but the primary issue is that she was task-fatigued and simply looking for the exit. This is a testing-shell problem, not an app problem, but it invalidates the Task 2 measurement.

The key changes to make before the next session: (1) make "Generate AI Glossary" the primary CTA on the Glossary screen; (2) add a language-pair selector at onboarding; (3) relocate the "I'm Done" button or mirror it within the app viewport; (4) consider adding contextual help text to the AI feature to make its purpose explicit.

---

## 6. One Annotated Visual: Task Flow Comparison

```
TASK 1 — "Create an AI-generated glossary"

INTENDED PATH:                          ACTUAL PATH (Participant 1):
  Glossary screen                         Glossary screen
       ↓                                        ↓
  [Generate AI Glossary] ← PRIMARY       [Quick Add Term] ← USER WENT HERE
       ↓                                        ↓
  Describe appointment                    Add Term screen
       ↓                                        ↓
  AI builds glossary                      Saved "Cardio → Cardio" manually
                                                 ↓
                                           Task ended (15 sec, no AI used)

  ★ FIX: Make "Generate AI Glossary" visually dominant.
    Move "Quick Add Term" to secondary/overflow action.
```

```
TASK 3 — "Study at least 3 flashcards"

PATH (Participant 1 — SUCCESSFUL, independent):
  Glossary screen
       ↓
  Glossary Detail (Medical — Orthopedic)
       ↓
  [Study from detail] → Study screen
       ↓
  Card 1: tap → reveal → "Good" (4s)
  Card 2: tap → reveal → "Good" (1s)
  Card 3: tap → reveal → "Good" (1s)
       ↓
  task3_threshold_reached ✓
  "I'm done" clicked ✓ (total: 35 sec)

  ★ KEEP: This flow is clean. Users arrive here naturally and succeed.
```

---

*Word count (narrative sections only): ~750 words*
