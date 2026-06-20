---
name: opinion-article-writer
description: >
  Interactive skill for brainstorming, structuring, and drafting newspaper opinion articles,
  op-eds, columns, and commentary pieces. Use this skill whenever the user wants to write
  an opinion article, op-ed, commentary, or newspaper column — or whenever they ask for
  help developing an argument, finding an angle, writing a lede, structuring an op-ed,
  drafting a nut graf, finding a hook, or turning a topic into a publishable take.
  Also trigger when the user says things like "help me write an opinion piece", "I have an
  idea for an article", "I want to pitch a piece to [newspaper]", "help me write a column",
  "I want to write a commentary on X", "turn my idea into an op-ed", or "what's a good
  angle for an article about X". Always trigger for expert writers (academics, economists,
  researchers) who want to translate their expertise into accessible public commentary —
  even if they don't use the word "op-ed". When in doubt, trigger.
---

# Opinion Article Writer

A skill for brainstorming, structuring, and drafting newspaper opinion pieces, op-eds,
columns, and commentary articles.

## Overview

Opinion writing is a distinct craft that differs fundamentally from academic, technical,
or journalistic writing. This skill guides the user through a structured workflow:

1. **Clarify** — understand the user's idea, expertise, and target outlet
2. **Sharpen** — turn a topic into a clear, contestable argument
3. **Structure** — build the four-part skeleton (lede → nut graf → body → kicker)
4. **Draft** — produce a complete first draft
5. **Edit** — apply the five-pass editing system

Run these stages in order unless the user is already mid-process (e.g. they have a draft
and want editing help — skip straight to Stage 5).

---

## Stage 1 — Clarify

Before writing a word, gather three things:

**A. The idea or topic** — What does the user want to write about? A news event? A policy
issue? A personal observation? An academic finding they want to make accessible?

**B. The expertise** — What does the user know that a general reader doesn't? What is their
professional or lived vantage point? This is the *reason* they should write the piece, not
just anyone.

**C. The target outlet** — Who is the audience? This determines word count, tone, and how
much framing/context to include.

| Outlet type | Word count | Tone | Audience |
|---|---|---|---|
| National newspaper (e.g. Kathmandu Post) | 700–900 | Accessible, direct | Educated general public |
| Regional/specialist (e.g. The Wire, VoxDev, East Asia Forum) | 800–1,200 | Analytical but readable | Policy/academic community |
| Global platform (e.g. Project Syndicate, The Guardian) | 900–1,100 | Authoritative, globally framed | International educated readership |
| Online/blog outlet | 600–900 | Conversational | Urban, digital-native readers |

If the user hasn't specified an outlet, ask — or default to a quality national newspaper
and note the assumption.

---

## Stage 2 — Sharpen the Argument

The single most important step. A topic is not an argument. An argument is a specific,
contestable claim that a reasonable person could disagree with.

**The Topic → Argument ladder:**

| Level | Example |
|---|---|
| Topic | Civil servant salaries |
| Theme | The difficulty of public sector pay in a constrained fiscal environment |
| Question | Should Nepal increase civil servant salaries? |
| **Argument** | Nepal's salary freeze is not fiscal discipline — it is a self-funding corruption machine that costs the government more than a pay revision ever would |

Only the **Argument** level is publishable. Help the user climb the ladder.

**Three questions to find the argument:**

1. **What does everyone assume about this topic — and is that assumption wrong?**
   The counter-intuitive argument is the most powerful format. What does the user know,
   from expertise or data, that complicates the conventional wisdom?

2. **What are the second-order consequences nobody is talking about?**
   Most public commentary stops at the obvious first-order effect. The expert writer's
   value is pushing past that to the second and third-order consequences.

3. **Who is the overlooked victim or overlooked beneficiary?**
   Strong pieces often identify a group, institution, or future generation whose interests
   are not represented in the conventional debate.

**The one-sentence test:** The argument must be stateable in under 25 words, with no hedging.
If it can't pass this test, it isn't sharp enough yet.

❌ *"The government's approach to compensation may have some unintended consequences over the medium term."*
✅ *"Nepal's salary freeze is a corruption subsidy — and the country pays for it at ten times the cost of a pay revision."*

**Timeliness check:** Why does this argument need to be made *today*? Every strong op-ed
connects a durable argument to a specific, current event: a budget, a report, a protest,
an election, a new data release. If there is no current hook, either find one or help the
user identify the right timing.

---

## Stage 3 — Structure

Every strong opinion piece follows a four-part skeleton. Build this before drafting.

### Part 1 — The Lede (40–60 words, 1–3 sentences)

The single most important real estate in the piece. It must make the reader *need* to
continue. Four types:

- **Anecdote lede** — a short, vivid human story that embodies the argument
- **Counter-intuitive lede** — opens by saying something that surprises
- **News hook lede** — ties the argument to something that happened this week
- **Direct provocation lede** — states the argument boldly, immediately

The worst possible lede for academic writers: background and context. Never start there.

### Part 2 — The Nut Graf (50–70 words, 2–4 sentences, paragraph 2 or 3)

States the central argument explicitly. Does three things:
- States the claim plainly
- Signals why it is timely or urgent
- Previews (lightly) how the case will be made

This is the thesis. In academic writing it would appear on page 4. In an op-ed, it appears
in paragraph 2.

### Part 3 — The Body (4–6 paragraphs)

Rules:
- One idea per paragraph. Never two.
- 2–4 sentences per paragraph. White space is the reader's friend.
- Evidence woven in naturally, not footnoted.
- Include one **"to be sure" paragraph** — steelman the opposing view, then rebut it.
- Maximum 2–3 data points total. Choose the strongest and let them do the work.

**Standard body structure for a 750-word piece:**

| Paragraph | Job |
|---|---|
| Body §1 | First pillar of the argument |
| Body §2 | Second pillar / supporting evidence |
| Body §3 | "To be sure" — steelman the opposing view |
| Body §4 | Rebuttal / why the argument still holds |
| Body §5 | Implication — what should happen |

**Word count map:**

| Section | Words | % of piece |
|---|---|---|
| Lede | 40–60 | ~7% |
| Nut graf | 50–70 | ~8% |
| Body §1 | 80–100 | ~12% |
| Body §2 | 80–100 | ~12% |
| Body §3 (to be sure) | 60–80 | ~9% |
| Body §4 (rebuttal) | 80–100 | ~12% |
| Body §5 (implication) | 80–100 | ~12% |
| Kicker | 30–50 | ~6% |
| **Total** | **~700–750** | 100% |

### Part 4 — The Kicker (30–50 words, 1–3 sentences)

The closing punch. It should feel like a door closing firmly, not trailing off.

Three techniques:
- **Echo the lede** — return to the opening anecdote or image with new meaning
- **Issue a challenge** — a question or call to action that stays with the reader
- **End on a single resonant sentence** — short, active, implication-rich

What never to do: summarise what was just said.

---

## Stage 4 — Draft

Once the argument is sharp and the structure is agreed, write the full first draft.

**Drafting principles:**
- Write the nut graf first if the user is stuck — everything else scaffolds around it
- The lede can be written last (many professionals do this)
- Do not stop to edit during drafting — momentum matters
- Label each section (LEDE / NUT GRAF / BODY §1 etc.) while drafting so the user can see
  the structure clearly

**Voice and style rules for the draft:**

| Academic habit | Newspaper replacement |
|---|---|
| Passive voice | Active voice — actor first, then action |
| Long sentences (40+ words) | Vary length — short after long; 3 long = too many in a row |
| Abstract nouns (capacity, utilisation) | Concrete images — what does this look like in a person's life? |
| Hedging (may suggest, could indicate) | Direct statement — maximum one hedge per piece, in the "to be sure" |
| Jargon | Plain translation in the same sentence, or replace entirely |
| "I think that" / "In my opinion" | State the view directly; it's an opinion piece — this is implicit |

**Evidence rules for the draft:**

- **One killer number** — specific, surprising, human-scale. Place it in paragraphs 2–4.
  A killer number is the statistic that most surprised the writer when they first encountered it.
- **Maximum five to six data references** in the entire piece
- Source names that a general reader recognises: World Bank, IMF, national statistics
  offices, central banks — not working papers or conference proceedings
- Interpret every number — don't just state what it says, explain what it *means*

**The commodity wage device** (powerful for economics topics): Instead of citing percentages,
express a salary or value in terms of a basic good — rice, bread, a cylinder of cooking gas.
This makes abstract economic decline visceral and universally understood.

---

## Stage 5 — Edit

Five passes. Each pass has one job. Do not combine them.

**Pass 1 — Argument Pass** (logic only, not language)
- Is there one central claim, stated clearly, by paragraph 2–3?
- Does every paragraph have a clear argumentative job?
- Is the sequence the most persuasive order?
- Is any point repeated? If so, cut the weaker instance.

**Pass 2 — Opening Pass** (lede and nut graf only)
- Does the lede create forward pressure — curiosity, surprise, or provocation?
- Is the argument stated explicitly by paragraph 2 or 3?
- Would a general reader understand the argument after reading only three paragraphs?

**Pass 3 — Sentence Pass** (language only, not argument)
- Convert every passive construction to active voice
- Break any sentence over 35 words into two; insert a short sentence after three long ones
- Replace every abstract noun with a concrete image
- Remove every hedge except one (in the "to be sure" paragraph)
- Replace or translate every piece of jargon
- Count words — if over target, cut the two weakest paragraphs, then the three weakest sentences

**Pass 4 — Kicker Pass** (final paragraph only)
- Does it end with forward momentum, not a summary?
- Can the final sentence stand alone as a memorable single line?
- Does it echo the opening without merely repeating it?

**Pass 5 — Cold Read** (full piece, as a stranger — after minimum 2 hours away)
- Note the moment of confusion
- Note the moment of boredom
- Note any sentence that "tries too hard"
- Note any jump in logic without a bridge
- Fix only those four things. Stop.

---

## Editing Checklist (for the user to use on every piece)

**Argument**
- [ ] Central claim statable in one sentence, under 25 words
- [ ] Argument appears by paragraph 2 or 3
- [ ] Every paragraph has a clear argumentative job
- [ ] No paragraph repeats a point made elsewhere
- [ ] "To be sure" paragraph present, brief, followed by rebuttal
- [ ] Sequence is the most persuasive order

**Opening**
- [ ] Lede creates curiosity, surprise, or provocation
- [ ] No historical context before the argument
- [ ] General reader understands the argument within three paragraphs

**Language**
- [ ] No passive constructions remaining
- [ ] No sentence over 35 words without a short sentence following
- [ ] No abstract nouns left untranslated
- [ ] No jargon left unexplained
- [ ] Maximum one hedge in the entire piece
- [ ] Word count within target range

**Evidence**
- [ ] One killer number — specific, surprising, human-scale
- [ ] Maximum five to six data references total
- [ ] Every source named in a way a general reader recognises
- [ ] Every number explained, not just stated

**Kicker**
- [ ] No summary or conclusion language
- [ ] Ends on a single, memorable sentence
- [ ] Creates forward momentum, not backward reflection

**Final**
- [ ] Read aloud once — stumbling points are rewriting points
- [ ] Cold read completed after minimum two hours away
- [ ] Author biography prepared: two sentences, credentials only

---

## Common Patterns to Recognise

**The academic writer's signature mistakes:**
1. Slow opening — context before argument
2. Argument buried in the middle or end
3. Over-hedging throughout
4. Passive voice and nominalisation everywhere
5. Data dump — many numbers, no interpretation
6. Kicker that summarises instead of closes

**Counter-intuitive argument formats** (the most publishable type):
- "Everyone assumes X. The data shows Y."
- "The government is treating this as problem A. It is actually problem B."
- "The obvious victim here is X. The overlooked victim is Y."
- "This policy saves money on line item A. It costs ten times that on line item B."

---

## Workflow Summary

| Stage | Activity | Output |
|---|---|---|
| 1. Clarify | Understand topic, expertise, outlet | Shared context |
| 2. Sharpen | Find the contestable one-sentence argument | The take |
| 3. Structure | Build lede type, nut graf draft, body map, kicker idea | The skeleton |
| 4. Draft | Write complete first draft | The raw material |
| 5. Edit | Five passes | The publishable piece |

The user may arrive at any stage. Jump in at the right point.
