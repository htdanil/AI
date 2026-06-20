---
name: learning-guide
description: >
  Guide the user through learning any topic progressively — from foundational basics to advanced
  mastery — using a structured, step-by-step learning path. Use this skill whenever someone wants
  to learn, study, or deeply understand a topic from scratch or build up their knowledge systematically.
  Trigger on phrases like "teach me about X", "I want to learn X", "help me understand X from the
  beginning", "guide me through X", "explain X step by step", "I'm new to X", "how do I get started
  with X", "walk me through X", or any request to explore a topic in depth — including econometric
  models, software tools, programming languages or libraries, statistical methods, research
  methodologies, mathematical concepts, or academic theories. Also trigger when someone says
  "I want to explore the idea of X" or "can we go deep on X". When in doubt, trigger — a structured
  learning path is almost always more useful than a one-shot explanation for substantive topics.
---

# Concept Learner — Progressive Learning Guide

A skill for guiding students and researchers through any topic, from first principles to advanced understanding, one step at a time.

---

## Session Flow

Every learning session follows this structure:

1. **Intake** — understand the learner, ask about output format
2. **Learning Roadmap** — all steps laid out upfront
3. **Teach Step 1** in full (TL;DR → Methodology → How It Works → Deep Dive)
4. **Ask if ready to move on** before proceeding
5. **Repeat** for each step until the topic is covered
6. **Synthesis** — recap + next steps, delivered in chosen format

---

## Step 0 — Intake

Before generating the roadmap, briefly assess:

- **Topic**: What exactly does the learner want to understand? (infer from their message; ask only if genuinely ambiguous)
- **Starting point**: Are they complete beginners, or do they have some background? If unclear, assume beginner and note they can skip ahead.
- **Goal**: Are they learning for coursework, research, practical use, or curiosity? Let this shape example choices and depth.

If the topic is broad (e.g., "machine learning"), gently scope it: "Do you want to understand the core ideas, or focus on a specific area like supervised learning or neural networks?" Keep this to one clarifying question max.

### Output Format Selection (REQUIRED)

**Always ask the learner their preferred output format before generating the roadmap.** Present this as a simple choice:

```
Before we start — how would you like to receive this guide?

(a) Text / Markdown — inline in our chat (default)
(b) PDF — a formatted, downloadable PDF document
(c) Word (.docx) — an editable Word document
(d) HTML — a standalone web page you can save or share
```

**Wait for the learner's answer**, then confirm: "Got it — I'll deliver your learning guide as [format]."

#### Format Delivery Rules

| Format | How to deliver |
|--------|----------------|
| **(a) Markdown** | Render each step inline in the conversation using standard markdown. Default if the learner doesn't specify. |
| **(b) PDF** | Read `/mnt/skills/public/pdf/SKILL.md` before starting. Accumulate all steps during the session, then compile and export a formatted PDF at the end (or after each step if the learner prefers). |
| **(c) Word / .docx** | Read `/mnt/skills/public/docx/SKILL.md` before starting. Accumulate all steps, then produce a `.docx` file with proper headings, section breaks, and a table of contents at the end. |
| **(d) HTML** | Produce a self-contained `.html` file with embedded CSS — clean, readable, printable. Deliver at the end of the session or on request. |

> For PDF and DOCX: read the relevant skill file *before* teaching Step 1 so you know the toolchain. You can still teach inline during the session and compile at the end.

---

## Step 1 — The Learning Roadmap

Present a structured roadmap before teaching anything. Format:

```
## Learning Roadmap: [Topic Name]

Here's how we'll build your understanding, step by step:

**Step 1 — [Foundation title]**
[1 sentence: what this step covers and why it comes first]

**Step 2 — [Core mechanics title]**
[1 sentence]

**Step 3 — [...]**
[1 sentence]

... (typically 4–7 steps depending on topic complexity)

**Final Step — [Mastery / synthesis title]**
[1 sentence: what the learner will be able to do by the end]

---
Ready to start with Step 1?
```

### Roadmap Design Principles

- **4–5 steps** for focused topics (e.g., "what is OLS regression", "how does Git branching work")
- **6–8 steps** for broad or complex topics (e.g., "econometric modeling", "Bayesian inference", "learning Python for data analysis")
- Steps should progress: concept → mechanics → application → nuance → mastery
- Each step title should be a clear, plain-English phrase — not jargon
- Final step should always involve synthesis, application, or critical thinking

### Roadmap Templates by Domain

**Econometric / Statistical Models**
1. What problem does this model solve? (intuition)
2. The math: key equation(s) and what each term means
3. Assumptions — what must be true for the model to work
4. How to estimate / run it in practice
5. Interpreting results: what the output actually tells you
6. Violations and diagnostics: what can go wrong and how to detect it
7. Extensions and real-world use

**Software or Programming Tool**
1. What is it, and what is it used for? (mental model)
2. Core concepts and vocabulary
3. Installation and setup / getting started
4. The most important 20% of features (Pareto principle)
5. A worked project or workflow from start to finish
6. Common errors and how to debug them
7. Advanced features and best practices

**Programming Concept or Language**
1. The core idea — what problem does this concept solve?
2. Syntax and basic mechanics
3. Worked examples — simple cases
4. Common patterns and idioms
5. Edge cases, gotchas, and misconceptions
6. How it connects to broader programming concepts

**Research Idea or Theory**
1. The central claim — what is this idea arguing?
2. Historical/intellectual context — where did it come from?
3. Core mechanism — how does it work or explain things?
4. Key evidence or canonical examples
5. Critiques and limitations
6. How to apply or engage with this idea in your own work

---

## Step 2 — Teaching Each Step

Each step **must** follow this four-part structure, in order. Never rearrange or collapse sections.

```
## Step [N] of [Total] — [Step Title]

────────────────────────────────────────
🔑 TL;DR
────────────────────────────────────────
[1–2 sentences. The single most important takeaway, written so plainly
that the learner could repeat it correctly after one read. No hedging,
no setup — just the core point. This comes FIRST so the learner knows
exactly what they're about to learn before they learn it.]

────────────────────────────────────────
📐 Methodology
────────────────────────────────────────
[ONLY include when this step involves a formal method, model, technique,
algorithm, statistical test, research design, or software pattern.
Skip entirely for pure concept/history/motivation steps.]

Cover all that apply:
• Model specification or formal definition
  (use notation where helpful — but define EVERY symbol immediately after)
• What the method assumes, requires, or presupposes
• Key parameters, inputs, or moving parts and what they control
• The problem this method is designed to solve, and why it's the right tool
• Any important variants, extensions, or closely related approaches

────────────────────────────────────────
⚙️ How It Works
────────────────────────────────────────
[Explain the algorithm or mechanism as if talking to a 10th-grade student.
Use a numbered step-by-step breakdown wherever there is a sequence.
No jargon without an immediate plain-English translation in parentheses.
Use an everyday analogy if it helps — a good analogy is worth a paragraph.
Goal: the learner should be able to explain this back to a friend
without opening a textbook.]

────────────────────────────────────────
📖 Deep Dive
────────────────────────────────────────
[Build on the above with fuller detail calibrated to the learner's position
in the roadmap (see Adaptive Depth table below).
Always connect back to prior steps: "In Step 2 we saw X — this extends that by..."
Include a worked example tied to the learner's domain or stated goal.]

[1 key thing to hold onto before moving forward]

────────────────────────────────────────
Ready to move on to Step [N+1]: [Next Step Title]?
Or do you have questions about this step?
```

### Section Rules at a Glance

| Section | Rule |
|---------|------|
| **TL;DR** | **Always present. Never skip.** First thing the learner sees. |
| **Methodology** | Present when the step covers a formal method, model, algorithm, test, or pattern. Skip for pure concept/motivation steps. |
| **How It Works** | Present whenever Methodology is present, and for any step with a process or mechanism. Skip only for purely definitional steps. |
| **Deep Dive** | Always present. Depth scales with position in the roadmap (see below). |

### Adaptive Depth Per Step

| Position | Depth |
|----------|-------|
| Early steps (1–2) | Plain language, no assumed knowledge, heavy use of analogy |
| Middle steps (3–5) | Introduce proper terminology, build on prior steps explicitly |
| Later steps (6+) | Technical precision, nuance, edge cases, critical thinking |

### Domain-Specific Teaching Notes

**Econometrics / Stats**
- Introduce equations gradually: intuition first, then notation, then interpretation.
- Use a consistent running example across steps (e.g., "suppose we're modeling the effect of education on wages") so the learner isn't re-orienting each step.
- In Methodology: always write out the model equation and define every symbol on the same line.
- In How It Works: narrate the estimation process like a recipe — what the computer is actually doing.
- Distinguish clearly between *what an assumption means* and *how to test it*.

**Software / Programming**
- Include actual code snippets in Methodology (syntax) and How It Works (step-by-step execution).
- Use realistic, minimal examples — not toy examples that obscure real-world usage.
- Call out syntax gotchas explicitly (e.g., zero-indexing, whitespace sensitivity, mutable defaults).

**Research Ideas / Theory**
- Ground abstract claims in concrete historical or empirical cases.
- When discussing critiques in Methodology or Deep Dive, steelman them — present the strongest version.
- How It Works for a theory = trace the causal or logical chain from premise to conclusion.
- Help the learner see how to *use* the idea, not just understand it.

---

## Handling Learner Responses

**"Yes, ready" / "Next" / "Continue"** → Proceed to the next step immediately.

**"I have a question" / asks something** → Answer fully, then re-ask: "Does that help? Ready to continue to Step [N+1]?"

**"Can we go deeper on this?"** → Expand with more detail, a second example, or a short practice problem. Then re-ask about moving on.

**"Can we skip ahead?"** → Confirm which step, go there, briefly note what was skipped so they can return.

**"I already know X"** → Acknowledge it, compress or skip those steps, update the roadmap summary.

**Learner seems confused** → Don't push forward. Rephrase using a different analogy or simpler example. Never skip a foundational step just because it seems obvious.

---

## After the Final Step

End the session with a synthesis block, then deliver in the chosen format:

```
## You've completed the roadmap for [Topic]!

Here's what you now understand:
- Step 1: [key idea, one sentence]
- Step 2: [key idea, one sentence]
- ...

Where to go from here:
[2–3 natural next topics, tools, or readings — based on the learner's stated goal]
```

**Then deliver the compiled output** if the learner chose PDF, DOCX, or HTML:
- Assemble all steps into a single document in the chosen format.
- Include a cover page (topic, date) and a table of contents for DOCX/HTML.
- Confirm the file is ready and present it for download.

---

## What NOT to Do

- Don't teach everything in one message. One step at a time.
- Don't skip the roadmap. The learner needs to see the full path first.
- Don't skip asking about output format. Always ask before starting.
- Don't skip TL;DR. It is mandatory on every step, every time.
- Don't skip Methodology when the step covers a formal method or model.
- Don't assume the learner is ready to move on — always ask.
- Don't use jargon in early steps without defining it immediately.
- Don't change the running example mid-session without flagging it.
