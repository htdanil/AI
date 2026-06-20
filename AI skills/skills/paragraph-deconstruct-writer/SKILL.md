---
name: paragraph-deconstruct-writer
description: >
  Use this skill whenever a user wants to improve academic writing for research papers in economics or social sciences, especially to avoid AI detection and sound more human-like. Trigger this skill when the user provides a paragraph or bullet points and asks to rewrite, improve, humanize, or paraphrase their academic writing. Also trigger when the user mentions AI detection, AI-sounding text, or wants writing that sounds more natural or authentic. This skill follows a two-step process: (1) deconstruct a paragraph into key-idea bullet points, then (2) reconstruct a polished, human-like academic paragraph from those bullets.
---

# Paragraph Deconstruct & Writer

A skill for improving academic writing in economics and social sciences by deconstructing paragraphs into key ideas and reconstructing them in a natural, human-like style that avoids AI detection patterns.

---

## Workflow

### Step 1 — Deconstruct (skip if user provides bullet points)

If the user provides a **paragraph**, extract one bullet point per sentence capturing the core idea. Keep bullets factual and concise — don't add interpretation. Present them to the user and ask:

> "Here are the key ideas I've extracted. Feel free to edit, reorder, or add any points before I reconstruct the paragraph."

Wait for the user to confirm or revise before proceeding to Step 2.

If the user provides **bullet points directly**, skip to Step 2 immediately.

---

### Step 2 — Reconstruct

Reconstruct a full academic paragraph from the confirmed bullet points. Follow all guidance below.

---

## Writing Principles for Human-Like Academic Prose

### Voice and Tone
- Write with **authorial confidence** — take positions, don't just report. Use "This paper argues…" or "The evidence suggests…" not "It can be noted that…"
- Let the writer's reasoning show through sentence structure, not hedging phrases
- Avoid an overly detached or encyclopaedic tone; economics writing has a clear argumentative voice

### Sentence Variety (critical for human feel)
- **Mix short and long sentences** deliberately. A short sentence after a long one creates emphasis. Don't make every sentence the same length.
- Occasionally open a sentence with a conjunctive word like "But", "Yet", or "And" — real academic writers do this
- Vary how sentences begin: don't always start with the subject. Use participial phrases, prepositional openers, or subordinate clauses
- Avoid perfect parallel structure across every sentence — humans are slightly irregular

### Transitions and Flow
- Use **specific, functional transitions** tied to the logic: "This gap explains why…", "As a result, registration rates…", "Taken together, these factors…"
- Avoid generic transition words that AI overuses: *Furthermore, Moreover, Additionally, It is worth noting, It is important to highlight, In addition to this*
- Connect ideas through **reference and repetition** of key terms rather than transition words alone

### Word Choice — Words and Phrases to AVOID
These are strongly associated with AI-generated text. Never use them:

| Avoid | Use instead |
|---|---|
| utilize | use |
| leverage (as verb) | draw on, apply, build on |
| delve into | examine, explore, look at |
| crucial / pivotal / vital | important, central, key, significant |
| multifaceted / nuanced | complex, varied, uneven |
| robust | strong, reliable, consistent |
| comprehensive | broad, wide-ranging, full |
| it is worth noting | (just say the thing) |
| navigate (metaphorically) | address, manage, handle |
| foster | support, promote, build |
| underscores / underscoring | shows, confirms, reflects |
| in today's world / in the modern era | (omit or be specific) |
| tapestry / landscape / ecosystem (metaphors) | (omit; use plain description) |
| cutting-edge | recent, new, advanced |

### Sentence-Level Patterns to AVOID
- Pairs of balanced clauses: "While X is important, Y is equally significant" — AI loves these
- Three-item lists that end every point: "…efficiency, equity, and sustainability"
- Ending paragraphs with a grand summary sentence that restates everything just said
- Opening with a sweeping universal claim ("Across the globe…", "Throughout history…")
- Passive constructions stacked back-to-back

### Economics/Social Science Conventions to PRESERVE
- Use precise quantitative language when available: "a 20 percentage point gap" not "a large gap"
- Cite mechanisms, not just correlations: explain *why* something happens
- Be direct about causality claims vs. association
- Use discipline-standard terms (regression, endogeneity, panel data, etc.) naturally — don't simplify jargon that belongs in the field

---

## Output Format

Present the reconstructed paragraph as plain text (no bullet points, no headers). Then add a brief note below:

> **Changes made:** [2–3 sentences describing the main structural or stylistic choices — e.g., "Shortened the opening sentence for impact. Replaced 'Furthermore' with a causal connector. Broke the third sentence into two to vary rhythm."]

Ask the user: "How does this feel? I can adjust the tone, tighten any sentences, or rework specific phrases."

---

## Example (for reference only — do not reuse this content)

**Input bullet points:**
- CRVS is necessary for legal identity and good governance
- Universal birth registration is a must in developing countries to guarantee human rights and ensure efficient service delivery
- The "Get Everyone in the Picture" initiative was formalized in 2014 in the Asia-Pacific region

**Reconstructed paragraph:**
Civil registration and vital statistics (CRVS) systems underpin both legal identity and effective governance. In developing countries, universal birth registration is not merely an administrative goal — it is a precondition for protecting human rights and delivering public services equitably. Recognising this, Asia-Pacific governments formalised their commitment in 2014 through the "Get Everyone in the Picture" initiative, a decade-long regional effort to close persistent registration gaps.

**Changes made:** Replaced the flat opening with a more assertive claim. Added an em-dash to create emphasis in the second sentence rather than a plain clause. Used "Recognising this" to tie the third sentence causally to the second rather than starting with a generic transition.
