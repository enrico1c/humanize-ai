---
name: humanize-ai
description: Rewrite AI-generated English text into natural human prose — eliminating AI fingerprints (delve, leverage, em-dashes, symmetrical bullet dumps, filler openers), matching the target register (academic, professional, or casual), while preserving every fact exactly.
level: 3
---

# Humanize AI

Rewrite AI-generated English text into fluent, natural prose. Preserves every fact, number, citation, and structural claim exactly — changes only the language surface. Eliminates all AI-generation fingerprints (overused words, mechanical transitions, perfect sentence symmetry, bullet-to-prose dumps, filler openers) and replaces them with register-appropriate, idiomatic English.

## When to Use

Use this skill when:
- the user provides text, a PDF extract, docx content, or a draft and says "make it sound human", "humanize this", "remove AI tone", or similar
- the source was clearly written by an LLM (em-dashes everywhere, "delve into", "it's worth noting", every paragraph starting with "Furthermore")
- the goal is a specific register: academic paper, professional report, or natural casual prose
- the output must have no AI slop, no filler phrases, no mechanical symmetry

Do **not** use when:
- the user wants a translation, not a rewrite
- the source is already natural, polished English
- the user explicitly wants to keep a formal/structured LLM-style output

---

## Core Principles

### 1. Factual fidelity — zero tolerance for invention
Every number, citation, institution name, percentage, date, and proper noun must match the source exactly. If the source says "a 12.4% increase in Q3 2024", the output must preserve that — not "roughly 12% growth last year". If uncertain about a claim, keep the source wording verbatim inside the rewritten sentence.

### 2. AI word elimination — the banned list
These words and phrases are LLM fingerprints. Replace or restructure every instance:

**Overused single words:**
`delve` `leverage` (as verb meaning "use") `navigate` `explore` `unlock` `transform` `pivotal` `crucial` `comprehensive` `multifaceted` `robust` `streamline` `paramount` `cutting-edge` `state-of-the-art` `game-changing` `groundbreaking` `seamless` `innovative` `empowering` `nuanced` `intricate` `vibrant` `foster` `underscore` `testament`

**Filler openers and transitions:**
- "It's worth noting that" → delete and state the fact directly
- "It is important to note that" → delete
- "It is crucial to understand that" → delete
- "In today's [world / landscape / era / fast-paced environment]" → cut; start with the actual claim
- "In the realm of" → cut; name the field directly
- "The world of X" → cut
- "When it comes to X" → cut
- "First and foremost" → "First"
- "Last but not least" → "Finally"
- "At the end of the day" → delete or rephrase
- "Moving forward" → cut or "Going forward" if needed
- "In conclusion, it is clear that" → "In sum," or start the conclusion directly
- "Furthermore" / "Moreover" / "Additionally" at the start of every paragraph → vary with "Also,", "Beyond that,", "A second factor is", or no connective at all when the logic is obvious

**Structural tells:**
- Three parallel bullet points each starting with the same word → rewrite as prose
- Every sentence the same length (~20 words) → vary deliberately
- Opening paragraph that restates the question before answering → cut it; start with the answer
- Closing paragraph that summarises what was just said → cut or condense to one sentence

### 3. Register targeting
The skill supports three registers. The user specifies; default is **professional**.

| Register | Sentence style | Contractions | Passive | Hedging |
|---|---|---|---|---|
| `academic` | complex but readable; subordinate clauses | sparingly | allowed; "has been documented", "is considered" | formal: "evidence suggests", "it appears that" |
| `professional` | crisp; mix of short and medium | moderate (don't, it's, we've) | light; prefer active | measured: "likely", "typically", "in most cases" |
| `casual` | short sentences; conversational | free | rarely | light: "probably", "usually", "I'd say" |

### 4. Em-dash handling
Em-dashes (—) are the single most common AI fingerprint in English. Replace every instance:

| Source pattern | English replacement |
|---|---|
| `X — Y` (parenthetical) | `X, Y` or `X (Y)` or restructure as subordinate clause |
| `X — Y — Z` (nested aside) | rephrase as subordinate clause or split into two sentences |
| `— item` (bullet marker) | delete; item becomes a standalone sentence |
| `X —` (trailing) | `X,` or close the sentence |
| `which — by definition —` | `which, by definition,` |
| `results — particularly in Q3 —` | `results (particularly in Q3)` |

After replacement: clean up `, ,` → `,` · `: ,` → `:` · `,.` → `.` · `,;` → `;`

### 5. Sentence variety — the primary humanisation tool
Human writers mix sentence lengths naturally. LLMs produce uniform length. Fix this:
- After a long complex sentence (25+ words), write a short one (5–12 words).
- Fragments are acceptable in professional and casual registers: "Not always."
- Start sentences with conjunctions occasionally: "But this assumes…", "And yet…"
- Vary sentence openers: don't start three consecutive sentences with the subject noun.

### 6. Bullet-to-prose conversion
Bullet lists from the source must be absorbed into paragraphs. Use natural connectives:

**Additive:** also, beyond that, a further point is, on top of that, equally  
**Contrastive:** but, yet, however, even so, that said, on the other hand  
**Causal:** so, therefore, as a result, which means, this explains why  
**Sequential:** first … then … finally; to begin … next … in the end  
**Exemplificative:** for instance, take the case of, consider, as seen in  
**Concessive:** although, even if, granted that, admittedly, while  
**Reformulating:** in other words, put differently, to be specific, that is  

Exception: data tables, comparison grids, and structured reference lists stay as tables — do not prose-ify data.

### 7. Paragraph structure
Each paragraph should:
- Open with a concrete topic sentence (claim-first, not background-first)
- Develop with 2–4 supporting sentences of varying length
- Close with a consequence, implication, or transition — not a summary of what was just said
- Run 60–160 words (flexible; short paragraphs are fine in professional/casual)

### 8. English punctuation norms
- Quotation marks: "double" for quotes, 'single' for quotes within quotes (or follow source style)
- Oxford comma: use unless source style explicitly avoids it
- Decimal separator: period (3.8%, not 3,8%)
- Thousands separator: comma (1,000 not 1.000)
- En-dash for ranges: 2020–2024, pp. 12–15 (not em-dash, not hyphen)
- Hyphenated compounds: follow standard usage (`well-known`, `state-of-the-art` as adj, no hyphen as predicate)

---

## Workflow

### Step 0 — Understand the source
Read the full source before writing a single word. Identify:
- Document type (LLM draft / slide extract / raw PDF / rough notes)
- Target register (ask if not specified)
- AI fingerprints to eliminate: flag every banned word, em-dash, and filler opener
- Factual anchors: numbers, citations, proper nouns — these are untouchable

### Step 1 — Plan the output structure
Map source sections → output sections. If the source is a bullet-heavy slide deck, infer a prose structure (intro → body sections → conclusion). Show the user the planned structure before writing only if the source is large (>1,500 words) or structurally ambiguous.

### Step 2 — Rewrite section by section
For each section:
1. Cut or rewrite every filler opener (do not start with "In today's world")
2. Absorb bullets into flowing prose using the connectives palette
3. Eliminate em-dashes with the substitution rules above
4. Replace banned words — check the full list, not just the obvious ones
5. Vary sentence lengths deliberately
6. Verify every factual claim against the source

### Step 3 — Post-process pass
After drafting, run a final sweep:
- [ ] Zero em-dashes remaining (`—` count = 0)
- [ ] Every number/citation matches source
- [ ] No banned words from the AI word list
- [ ] No filler openers in any paragraph
- [ ] Sentence lengths vary within each paragraph
- [ ] No double commas, colon-commas, or period-commas
- [ ] Section structure complete (all source sections represented)
- [ ] Register consistent throughout

### Step 4 — Output format
If writing to a Word document (.docx), generate a Python script using `python-docx` that:
- Uses Calibri 11pt Normal style
- Uses Heading 1 (navy `#1F497D`) for h1, Heading 2 (blue `#2E74B5`) for h2
- Justifies all body paragraphs
- Adds tables with `'Table Grid'` style
- Outputs to the user-specified path

If writing to plain text, output raw markdown.

---

## English Academic Connectives Palette (extended)

**Contrast:** however, yet, that said, even so, by contrast, on the other hand, while this is true  
**Addition:** also, in addition, beyond this, a further consideration is, equally relevant  
**Cause/Effect:** therefore, as a result, consequently, it follows that, this explains  
**Sequence:** first, then, next, after that, finally, subsequently, at this point  
**Example:** for instance, for example, to illustrate, consider the case of, as seen in  
**Concession:** although, even though, granted, admittedly, while it is true that  
**Emphasis:** indeed, in fact, notably, above all, what matters here is  
**Summary/Closure:** in short, in sum, taken together, on balance, the upshot is  

---

## Quality Gates

Before delivering the output, verify:
1. **Factual accuracy** — spot-check 5 random facts against source
2. **Em-dash count** — search output for `—`; must be zero
3. **Banned words** — search for the top 10 most common offenders: `delve`, `leverage`, `crucial`, `comprehensive`, `seamless`, `robust`, `pivotal`, `foster`, `underscore`, `testament`
4. **Filler openers** — scan every paragraph's opening sentence; none may begin with a banned phrase
5. **Sentence variety** — scan any paragraph where all sentences are 18–22 words; rewrite at least one short (<12 words) and one longer clause in that block
6. **Register consistency** — no tonal breaks (no casual contractions in an academic section, no jargon in a casual section)
7. **Structure completeness** — all source sections represented

---

## Usage

```
/humanize-ai
```

Then paste or attach the source material. Optionally specify:
- Register: `--register academic` | `--register professional` (default) | `--register casual`
- Output format: `--docx <path>` or `--markdown` (default)
- Target section: `--section "3.2"` to rewrite only a specific section

### Example invocations

```
/humanize-ai --register academic

[paste LLM-generated essay extract]
```

```
/humanize-ai --register casual --markdown

[paste blog post draft that sounds robotic]
```

```
/humanize-ai --register professional --docx "C:/Users/.../report.docx"

[paste executive summary with heavy AI tone]
```

---

## What This Skill Produces

Input: AI-generated text with em-dashes, "delve into", "leverage", filler openers, uniform sentence lengths, bullet dumps masquerading as paragraphs.

Output:
- Natural prose in the specified register
- Zero em-dashes (verified)
- Zero banned AI words
- Varied sentence structure
- All factual claims intact and verbatim
- Optional .docx file via python-docx script

Sister skill: `/italian-rewriting` — same factual-fidelity and em-dash rules applied to academic Italian prose.
