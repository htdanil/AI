---
name: scholarly-paper-overview
description: >
  Fetches a scholarly source from a provided link (e.g., DOI, PDF URL, journal page) and produces a structured, one-page overview as a Markdown file — formatted for quick skimming and designed to support academic manuscript writing. Use this skill whenever the user provides a link to a paper, report, or scholarly source and asks for a summary, overview, breakdown, or review. Also trigger when the user says things like "summarise this paper", "give me an overview of this study", "break down this article", "what does this paper say about X", or pastes a DOI or URL and wants it unpacked. If the user specifies a focus area (e.g., methodology, findings, theory), the output should weight that section more heavily. Always use this skill when a scholarly link is provided — never rely on memory or training data to describe a paper's contents.
---

# Scholarly Paper Overview Skill

## Purpose
Fetch a scholarly source from a user-provided link and produce a **structured, one-page overview** as a `.md` file, designed to support academic manuscript writing. If the user specifies a focus area, that section receives extended treatment.

---

## Workflow

### Step 0 — Ask for a Focus Area (always do this first)

Before fetching anything, ask the user one short question:

> "Is there a specific area you'd like me to focus on — e.g., methodology, findings, theory, implications? Or should I give an equal overview of everything?"

Wait for their reply, then proceed. If they name a focus area, carry it through all subsequent steps.

---

### Step 1 — Fetch the Source

Use the following **priority order** to retrieve paper content. Move to the next source only if the previous one returns insufficient information (no abstract, no metadata, or no full text).

#### 1a. Consensus MCP (primary)
- Use **`Consensus:search`** to search for the paper by title, authors, or keywords from the DOI landing page.
- Consensus returns structured metadata: title, authors, year, abstract, journal, and sometimes methodology/findings summaries.
- Use this as the primary content source when available.

#### 1b. PubMed MCP (secondary — especially for biomedical/health papers)
Use PubMed MCP tools in this sequence:

1. **`PubMed:search_articles`** — Search by title keywords or author names to locate the article and get its PMID.
2. **`PubMed:get_article_metadata`** — Use the PMID to retrieve full structured metadata: title, authors, journal, year, abstract, MeSH terms, affiliations.
3. **`PubMed:get_full_text_article`** — If available via PubMed Central (PMC), fetch the full text for richer content extraction.
4. **`PubMed:convert_article_ids`** — If the user provides a DOI, convert it to PMID first using this tool, then proceed with steps 2–3.
5. **`PubMed:find_related_articles`** — Optionally use to surface closely related papers for the Relevance Note section.

PubMed is particularly useful for life sciences, medicine, public health, and clinical research papers.

#### 1c. web_fetch (fallback)
- If neither MCP returns sufficient content, fall back to `web_fetch`:
  - For DOI links, fetch `https://doi.org/<doi>` directly.
  - If the page is paywalled or inaccessible, fetch the abstract page and note limitations in the output.
  - If an open-access PDF is available, fetch and extract text from it.

#### Source logging
At the top of the output file, note which source was used:
`> 📥 Source: Consensus MCP` / `> 📥 Source: PubMed MCP` / `> 📥 Source: web_fetch` / `> 📥 Source: Multiple (Consensus + PubMed)`

### Step 2 — Produce the Overview
Write a structured Markdown file following the **template below**. Keep the overall output tight — **aim for ~400–600 words** (excluding the focus section). Prioritise bullet points and short table cells over prose. If the user named a focus area, expand only that section to 2–4 short paragraphs; keep every other section to 1 sentence.

---

## Output Template

```markdown
# Paper Overview
> 📥 Source: [Consensus MCP / PubMed MCP / web_fetch]  
> 🔍 Focus: [user's focus area, or "Equal overview"]

**Title:** Full paper title  
**Authors:** Last, F. et al. · **Year:** YYYY · **Journal:** Journal name  
**DOI/URL:** https://doi.org/...

---

## At a Glance

| | |
|---|---|
| **Research Question** | One sentence. |
| **Theory / Framework** | One sentence. |
| **Method** | Design · data source · sample size · analysis approach — one sentence. |
| **Key Findings** | 2–3 bullet points with key results or effect sizes. |
| **Contribution** | One sentence on what this adds to the literature. |
| **Limitations** | One sentence. |
| **Implications** | One sentence (policy / practice / theory). |
| **Future Research** | One sentence. |

---

## [FOCUS AREA] *(only if user specified one — remove otherwise)*

2–4 short paragraphs with deeper treatment. Include specific details, paraphrased evidence, figures, or arguments from the paper. Each paragraph should be ≤ 5 sentences.

---

## Cite-Ready Note
*One sentence: how to position this paper in a manuscript (e.g., theoretical grounding, empirical evidence, contrasting view, methodological reference).*
```

---

## Quality Rules

- **Tight by default**: Table cells are 1 sentence max (or 2–3 bullets for findings). No filler prose.
- **Focus area only expands the named section** — everything else stays 1 sentence.
- **No invented content**: Only include what is actually in the fetched source. If a section is absent, write "Not discussed."
- **Paraphrase only**: Never reproduce verbatim text from the source.
- **Inaccessible source**: If full text cannot be fetched, note clearly: `⚠️ Full text not accessible — based on abstract only.` and fill in what is available.

---

## Output Delivery

- Save the file as `paper_overview_<short_title>.md` in `/mnt/user-data/outputs/`
- Use `present_files` to deliver it to the user.
- After presenting, add a one-line note in chat about anything notable (e.g., "Full text was accessible" or "Only the abstract was available — you may want to check institutional access.").
