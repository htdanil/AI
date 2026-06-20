---
name: the-4-version-rewriting-helper
description: >
  Rewrites the user's writing into 4 distinct versions ranging from minimal correction to full creative rewrite. Use this skill whenever the user asks to "refine", "rewrite", "revise", "improve", "correct", or "polish" their writing — or when they share a paragraph, bullet points, or draft text and want multiple versions or options. Also trigger when the user says things like "give me different versions", "help me rewrite this", "can you revise this paragraph", or pastes text and asks for writing help. Always use this skill when the user provides raw text for revision, even if they don't explicitly ask for 4 versions.
---

# The 4-Version Rewriting Helper

When the user provides text for revision, produce exactly **4 versions** of the paragraph(s). Follow all instructions below precisely.

---

## Core Rules (Apply to ALL Versions)

- **Bold all modifications** — every changed, added, or restructured word/phrase must be in bold. Words retained unchanged stay in plain text.
- **No bullet points** — all versions must be written as prose paragraphs only.
- **Break paragraphs** wherever it aids readability and flow.
- **No new information** — do not add facts, claims, or ideas not present in the user's original text (except Version 2 feedback section, which may offer suggestions).
- **No AI clichés or filler** — strictly avoid phrases like "In today's world", "It is worth noting", "It goes without saying", "Delve into", "Tapestry of", "Navigating", "Unleash", "Moreover, it is important to…", and similar hollow constructions.
- **No predictable sentence structures** — vary rhythm and syntax naturally.

---

## Version Instructions

### Version 1 — Minimal Correction
Goal: Preserve the user's original voice, words, and style as much as possible.

Make only the corrections necessary for:
- Grammatical errors (subject-verb agreement, tense consistency, articles, prepositions)
- Spelling and punctuation
- Clearly vague or confusing word choices — replace only when the meaning is genuinely obscured
- Basic coherence: fix sentences that contradict each other or disrupt the logical flow

**Do not** restructure sentences, reorder ideas, or introduce synonyms for stylistic variety. The result should feel like the user's own writing, lightly cleaned.

---

### Version 2 — Feedback + Revised Draft
This version has **two parts**:

**Part A: Feedback**
Analyze Version 1 and provide a concise, structured critique in prose (no bullet points). Address all of the following where applicable:
- Grammatical, spelling, and punctuation issues remaining or newly noticed
- Vague or confusing words
- Redundant words or sentences
- Contradictions or logical inconsistencies
- Coherence and cohesion of the flow of ideas
- Vocabulary choices — suggest stronger or more precise alternatives
- Transition and connective words — identify where they are missing or weak
- Any other necessary corrections

Write the feedback as a flowing paragraph or short paragraphs, not a list.

**Part B: Revised Draft**
Rewrite the paragraph applying all the feedback from Part A. Bold all modifications relative to Version 1.

---

### Version 3 — Moderate Restructuring
Goal: Improve the writing meaningfully while staying grounded in the original.

You may:
- Rearrange the order of ideas for better flow
- Restructure sentences for clarity and rhythm
- Substitute words with more precise or varied alternatives
- Adjust transitions and connectives freely

Do **not** add new information. Aim for a noticeably improved version that still feels connected to the original material.

---

### Version 4 — Full Creative Rewrite
Goal: Produce the strongest possible version of the text.

You may:
- Entirely rewrite sentences and paragraph structure
- Reinvent the opening and closing
- Radically rephrase ideas for impact, clarity, or elegance
- Use inventive syntax and vocabulary

Do **not** add new information. The factual content must remain the same; only the expression changes. Aim for writing that is sharp, vivid, and memorable — avoid generic "elevated prose" in favor of something with genuine character.

---

## Output Format

Present the four versions clearly labeled. Use this structure:

---

**Version 1 — Minimal Correction**

[paragraph(s)]

---

**Version 2 — Feedback & Revised Draft**

*Feedback:*
[prose feedback]

*Revised Draft:*
[paragraph(s)]

---

**Version 3 — Moderate Restructuring**

[paragraph(s)]

---

**Version 4 — Full Creative Rewrite**

[paragraph(s)]

---

Do not add commentary before or after the versions unless the user asks a question. Deliver the four versions cleanly.
