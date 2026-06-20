---
name: brief-concept-explainer
description: >
  Instantly explain any concept, term, keyword, or idea in plain language — simply, briefly, and visually.
  Use this skill whenever the user provides a word, phrase, topic, or keyword and asks what it means, how it works,
  or wants it explained. Also trigger when the user says things like "explain X", "what is X", "break down X",
  "ELI5 X", "simplify X", or pastes jargon/terminology they want decoded. Always use this skill for concept
  explanations — never respond with long prose when a structured, brief breakdown would serve better.
---

# Brief Concept Explainer

## Purpose
Turn any keyword, term, or concept into a crisp, structured explanation — short enough to read in 30 seconds, rich enough to actually understand.

---

## Output Format (strict)

Every response must follow this exact structure, **under 200 words total**:

```
## [Concept Name]

**What it is**
- One-sentence plain-language definition.

**Analogy**
- Relatable real-world comparison. (e.g., "It's like...")

**How it works / Key points**
- Bullet 1
- Bullet 2
- Bullet 3 (max)

**Example(s)**
- Concrete illustrative example 1
- Numerical example (if applicable): show numbers/formula briefly

**🔗 Learn more**
- [Resource Name](URL) — one line description
- [Resource Name](URL) — one line description

---
[ASCII Mind Map — vertical, compact]
```

---

## Rules

1. **Brevity is law.** Hard cap: 200 words. Cut ruthlessly.
2. **No jargon** unless immediately defined.
3. **Analogy is mandatory** — always include one relatable comparison.
4. **Numerical example** — include if the concept is mathematical, financial, statistical, or measurable.
5. **1–2 examples** of the concept itself (beyond the analogy).
6. **Links** — always include 2 real, working URLs to quality resources (Wikipedia, Investopedia, Khan Academy, MDN, official docs, etc.) relevant to the concept.
7. **ASCII mind map** — always end with a vertical ASCII mind map showing the concept and its key branches. Keep it compact (under 15 lines).

---

## ASCII Mind Map Template

```
[CONCEPT]
    |
    ├── Definition: ...
    |
    ├── Analogy: ...
    |
    ├── Key Points
    |       ├── ...
    |       └── ...
    |
    ├── Examples
    |       ├── ...
    |       └── ...
    |
    └── Resources
            ├── ...
            └── ...
```

Adapt branches to the concept. Keep labels to 5 words or fewer per branch.

---

## Tone
- Friendly, smart, direct.
- Write like you're explaining to a curious 16-year-old.
- No hedging, no throat-clearing, no "Great question!"

---

## Example Output

**Input:** `Compound interest`

---

## Compound Interest

**What it is**
- Earning interest on both your original money *and* the interest already earned.

**Analogy**
- Like a snowball rolling downhill — it picks up more snow as it grows, faster and faster.

**Key points**
- Interest compounds over time: daily, monthly, or yearly.
- The longer you wait, the bigger the effect.
- Formula: A = P(1 + r/n)^(nt)

**Examples**
- $1,000 at 10%/yr for 30 years → ~$17,449 (not just $4,000)
- A savings account that reinvests its own returns each month.

**🔗 Learn more**
- [Khan Academy – Compound Interest](https://www.khanacademy.org/economics-finance-domain/core-finance/interest-tutorial) — free video lessons
- [Investopedia – Compound Interest](https://www.investopedia.com/terms/c/compoundinterest.asp) — full breakdown with examples

---
```
Compound Interest
      |
      ├── Definition: Interest on interest
      |
      ├── Analogy: Snowball rolling downhill
      |
      ├── Key Points
      |       ├── Grows over time
      |       ├── Reinvests earnings
      |       └── Formula: A = P(1+r/n)^nt
      |
      ├── Examples
      |       ├── $1k → $17k in 30 yrs
      |       └── Monthly savings account
      |
      └── Resources
              ├── Khan Academy
              └── Investopedia
```
