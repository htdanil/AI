---
name: relevant-literature-finder
description: >
  Find peer-reviewed academic papers, studies, and scholarly materials that support a specific
  statement, argument, finding, or claim provided by the user. Use this skill whenever a user
  provides a thesis statement, research finding, argument, or claim and asks for supporting
  academic literature. Trigger on phrases like: "find papers that support", "find literature for",
  "support this argument", "find studies supporting", "find academic evidence for", "I need
  references for", "what papers support the idea that", or any time the user shares an academic
  claim and wants backing evidence from the literature. Also trigger when the user says "find more
  papers" or "show more papers" after an initial search — this means they want 5 additional papers
  beyond what was already shown. If in doubt, trigger — finding supporting literature is almost
  always more useful than a generic response for academic users.
---

# Paper Support Finder

A skill for PhD-level researchers and academics to find peer-reviewed literature that supports a
specific statement, argument, finding, or discussion point.

---

## Workflow

### Step 1 — Parse the Statement

Carefully read the user's statement. Identify:
- **Core claim**: the central argument or finding to be supported
- **Key concepts**: 2–5 essential terms or constructs in the claim
- **Theoretical domain**: e.g., labor economics, institutional theory, behavioral finance
- **Mechanism or channel** (if present): e.g., "through credit constraints", "via peer effects"

If the statement is ambiguous or very broad, briefly flag this and ask for one clarifying detail
before proceeding. Otherwise, proceed directly.

---

### Step 2 — Build Search Queries

Decompose the statement into **3–5 distinct search queries** that together cover:
- The core claim phrased directly
- Key sub-mechanisms or mediating factors
- Related theoretical frameworks or foundational concepts
- Empirical applications (country-level, sector-level, or context-specific if implied)

**Good query design:**
- Keep queries to 4–8 words
- Vary phrasing across queries to avoid duplicate results
- Use academic terminology that would appear in abstract/title

---

### Step 3 — Search Consensus

Use the **Consensus MCP tool** to run each query. For the **initial request**, target retrieving
enough results to surface **10 high-quality, non-duplicate papers**.

Run queries one after another, collecting results. Track paper titles already shown to avoid
repeats across sessions or across "find more" calls.

---

### Step 4 — Select and Rank Papers

From the raw results, select the **best 10 papers** (or 5 for "find more" calls) using these
criteria, in order of priority:

1. **Relevance** — directly supports the user's statement as a main finding, argument, or result
2. **Quality** — published in peer-reviewed journals; prefer high-impact outlets
3. **Recency** — prefer recent work (last 10–15 years) unless seminal older papers are essential
4. **Diversity** — cover different methodologies (theory, empirical, experimental), contexts, and
   angles of the argument where possible
5. **Non-duplication** — do not repeat papers already shown in this conversation

Discard papers where the connection to the statement is weak or tangential.

---

### Step 5 — Format the Output

Present each paper in the following structured format. Number them sequentially across the entire
conversation (so "find more" continues from 11, 16, etc.).

---

**[N]. [Full Paper Title]**
- **Authors**: Last name, Initials; Last name, Initials (et al. if >3)
- **Year**: YYYY
- **Journal/Source**: Full journal name or working paper series
- **DOI**: Construct as `https://doi.org/[DOI]` if the DOI is available from the search result.
  If no DOI is returned, fall back to the **Consensus link** (URL from search results) labeled
  as "Access via Consensus". Never leave this field blank — always provide one or the other.
- **How it supports your statement**: 2–3 sentences explaining precisely how this paper's
  findings, arguments, or evidence back the user's claim. Be specific — cite the mechanism,
  context, or result that aligns with the statement.

---

After all papers, add a short **Search Strategy Note** (2–3 sentences) explaining the queries
used and any important gaps or limitations in the literature retrieved.

---

## "Find More Papers" Protocol

When the user says **"find more papers"**, **"show more"**, **"5 more"**, or similar:

- Do **not** repeat the full workflow from scratch
- Use the **same statement** from earlier in the conversation
- Run **new or refined search queries** not used before
- Return exactly **5 new papers**, numbered sequentially (e.g., 11–15, 16–20)
- Briefly note at the top: *"Here are 5 more papers supporting your statement (continuing from
  paper [N]):"*

---

## Quality Standards

- Never include a paper if you are uncertain it directly supports the statement
- Never fabricate or hallucinate paper details — only use papers returned by Consensus
- Never fabricate DOI links — only use DOIs explicitly present in the Consensus result. If
  absent, fall back to the Consensus URL. Do not guess or construct DOIs from paper metadata.
- If Consensus returns fewer high-quality results than needed, return what is available and
  transparently note the gap: *"Only [N] strong matches were found. The literature on this
  specific claim may be sparse — consider broadening the framing."*
- Always include the Consensus link so the user can verify and access the paper

---

## Tone and Style

- Write at PhD level — precise, direct, no filler
- Relevance explanations should be substantive and specific, not generic
- Do not editorialize beyond what the paper says
- Keep the Search Strategy Note factual and brief
