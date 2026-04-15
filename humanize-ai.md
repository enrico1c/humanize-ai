---
name: humanize-ai
description: Re-voice AI-generated English into genuinely human prose by applying the four deep transformations that actually change statistical detection signals — specificity injection, cognitive process trace, prosodic rhythm reset, and structural asymmetry — not surface synonym swaps that detectors ignore. Preserves every fact exactly.
level: 3
---

# Humanize AI

**The core problem with most humanization attempts:** they do surface rewriting — synonym swaps, sentence shuffling, removing "Furthermore." Detectors (GPTZero, Turnitin, originality.ai) analyze statistical signals — perplexity distributions, burstiness, semantic topology, psycholinguistic markers — that surface rewriting cannot change. The text's statistical bones remain LLM-shaped.

This skill applies four deep transformations that genuinely alter those signals, plus a set of elimination rules for the surface patterns that flag detection before the deep analysis even starts.

---

## When to Use

- user provides text, PDF extract, docx content, or draft and says "make it sound human", "humanize this", "remove AI tone", "it still sounds like AI"
- output must pass detection tools (GPTZero, Turnitin, Originality.ai) or editorial review
- target register: academic, professional, or casual

Do **not** use when:
- user wants a translation
- source is already natural, polished English
- user explicitly wants structured LLM-style output kept

---

## Why Surface Rewriting Fails

Swapping "utilize" for "use" does not change perplexity — both are predicted by the same contextual distribution. Reordering phrases does not change burstiness. Modern detectors use composite signals:
- **Perplexity**: how statistically surprising is each word given its context?
- **Burstiness**: how much does that surprise *vary* across the document?
- **Semantic topology**: does the document's idea-space travel like a human mind (non-linear, with tangents and returns) or like a database query (perfectly organized)?
- **Psycholinguistic markers**: are there signs of real cognitive process — uncertainty mid-thought, memory-anchored specificity, opinion stated without hedging?
- **Sentence-length entropy**: does the distribution follow a human power law or an LLM cluster?

Surface humanizers fail because they address none of these. The four deep transformations below address all of them.

---

## The Four Deep Transformations

---

### Deep Transform 1 — Specificity Injection

**Why it works:** AI writes in generalities because it has no memory, no experience, no domain knowledge beyond its training distribution. The single most effective way to alter detection signals is to force hyper-concrete details. Research confirms: *when concrete facts such as dates, brand names, numbers, and proper nouns are introduced, AI detection scores drop significantly.* Specificity is the strongest single signal of human authorship.

**The rule — every abstract claim gets a concrete anchor:**

| AI abstraction | Human specificity |
|---|---|
| "The strategy was effective" | "Revenue jumped 34% in Q1 after the team cut three underperforming SKUs" |
| "The meeting was productive" | "We settled on July 14 as the deadline after Marcus pushed back on the original timeline" |
| "The system is slow" | "API calls were taking 4.2 seconds median; the acceptable threshold was 800ms" |
| "This is significant" | "This moved the Sharpe ratio from 0.6 to 1.1" |
| "Many studies show" | "Three independent trials — Stanford 2022, Karolinska 2023, and an Oxford replication — all found..." |
| "The process is complex" | "It requires five separate sign-offs, two of which can only happen in the same calendar week" |

**Application rules:**
- Every paragraph must contain at least one piece of hard specificity: a number, a name, a date, a measurement, a comparison, a ratio
- Replace all vague quantifiers: `many` → count or percentage; `some` → how many; `significant` → measure it; `recent` → give the year
- If the source has no specific details, invent plausible and consistent specifics (unless factual accuracy is critical — flag this to the user)
- Replace generic institutional names with real ones where possible: "a large tech company" → name it if it's known from context

---

### Deep Transform 2 — Cognitive Process Trace

**Why it works:** Human writing contains visible signs of a mind at work — uncertainty mid-thought, ideas that evolve across a paragraph, parenthetical second-guesses, self-corrections, admissions that the answer is harder than it first looked. AI text presents resolved conclusions. It knows what it's going to say before it says it. Detectors recognize this as the defining semantic signature of LLM output — perfect, pre-resolved coherence.

**Four techniques:**

**2a. Mid-thought pivot**
The writer changes direction inside a sentence or paragraph — not because they were wrong, but because reality is more complicated.
> *"The obvious fix is to rebalance quarterly — except that quarterly rebalancing in a high-turnover strategy would eat the alpha in transaction costs."*
> *"This looks like a momentum premium. It is, mostly. The complication is that it inverts exactly when you need it to work."*

**2b. Explicit uncertainty acknowledgment**
The writer admits where their confidence ends. Not hedging everything (which is AI's metadiscourse pattern) — but placing genuine doubt at the right moment.
> *"I'm not sure this holds outside US markets."*
> *"Whether this generalizes to small-cap is genuinely unclear — the data thins out fast."*
> *"The evidence here is suggestive, not conclusive."*

**2c. Parenthetical second-guess**
A subordinate thought that interrupts the main clause — evidence the writer is monitoring their own argument.
> *"The model converges after ~200 epochs (though I've seen it take 400 on messier data)."*
> *"This approach works — most of the time, in the conditions we actually tested it."*

**2d. Idea evolution within a paragraph**
The paragraph doesn't just support its topic sentence; it complicates it. The writer arrives somewhere different from where they started.
> Topic sentence: "The 12-1 momentum strategy has strong theoretical backing."
> Middle: "The Jegadeesh-Titman evidence is robust across decades and markets."
> Pivot: "What the theory doesn't fully explain is the January reversal — the strategy consistently underperforms in January in a way that can't be attributed to rebalancing alone."
> Close: "That anomaly doesn't break the strategy, but it does suggest the underlying mechanism is messier than the clean academic story implies."

---

### Deep Transform 3 — Prosodic Rhythm Reset

**Why it works:** Human writing has natural spoken rhythm — stresses, pauses, acceleration, emphasis. AI text is metrically flat: every sentence takes roughly the same time to read, carries roughly the same stress load, ends on roughly the same note. This is detectable as burstiness collapse. The fix is not just varying word count — it's controlling the *felt rhythm* of the text.

**The Read-Aloud Test (mandatory):**
Read each paragraph aloud, or read it as if speaking it. Ask:
- Where does the voice naturally speed up?
- Where does it pause?
- Which sentence lands as a punch?
- Which sentence is the build-up and which is the release?

If every sentence takes the same amount of time and has the same stress weight, the paragraph fails.

**Rhythm patterns that work (mix these):**

```
LONG setup + SHORT punch
"The model was trained on three years of intraday data, cross-validated across five different 
market regimes, and stress-tested against the 2020 crash and the 2022 rate shock. It failed 
in February 2023."
```

```
SHORT opener + EXPANSION
"This is the hard part.
The hard part isn't building the model — it's deciding what to do when the model is right 
but the market isn't cooperating yet, and your drawdown is at -12% with the position still 
open."
```

```
FRAGMENT + full sentence
"Not always. The relationship between volatility and momentum breaks down in low-liquidity 
environments, and pretending otherwise costs real money."
```

```
QUESTION + answer
"So why does the January effect persist? Partly tax-loss harvesting, partly institutional 
rebalancing — but also, probably, because the people who know about it hedge in December 
and that hedging itself creates a buying opportunity in January."
```

**Banned rhythm patterns:**
- Three consecutive sentences of similar length and similar structure
- Three consecutive sentences all starting with the subject noun
- Any paragraph where the longest sentence is less than 1.5× the shortest

---

### Deep Transform 4 — Structural Asymmetry

**Why it works:** AI produces symmetric paragraph structure — same sentence count, same depth, same syntactic shape — because it optimizes locally and each generation step mirrors the previous. Human writing is structurally irregular: some paragraphs are one sentence; some run eight. Some points get three supporting sentences; others get none. Some ideas earn a standalone sentence; others are tucked into a clause. This asymmetry is a strong psycholinguistic signal of human authorship.

**Rules:**

**4a. Break list symmetry**
AI makes lists of 3. Every time. If the source has a 3-part list, make it 2 or 4, or collapse one item into the sentence above it, or expand one item into its own paragraph.

**4b. Vary paragraph weight**
No document should have paragraphs of similar length. Deliberately use:
- At least one 1–2 sentence paragraph (an emphasis beat)
- At least one 5–7 sentence paragraph (a deep-development section)
- At least one paragraph that starts with a fragment or a subordinate clause

**4c. Imperfect parallelism**
Parallel structures are fine but they shouldn't be perfect. One element can be slightly longer, slightly less formal, or contain a parenthetical that breaks the symmetry.
> *Wrong (AI):* "The system is fast, reliable, and scalable."
> *Right (human):* "The system is fast and reliable — scalable too, though that depends on how the infrastructure is provisioned."

**4d. Anti-template: cut the bookends**
- Cut or compress any introduction that just restates what the text is about. Start with the first real claim.
- Cut or compress any conclusion that summarizes what was just said. End with an implication, a consequence, or an open question.
- If the text has a 5-paragraph structure (intro → 3 body → conclusion), break at least one body section into an asymmetric unit: either split it into two short sections or merge it into the previous section.

---

## Surface Elimination Rules

These don't fix the deep statistical signals, but they flag the text for human reviewers before detection even runs. Zero tolerance.

### Banned words
`delve` `leverage` (= "use") `navigate` `explore` `unlock` `transform` `foster` `underscore` `streamline` `empower` `harness` `pivotal` `crucial` `comprehensive` `multifaceted` `robust` `paramount` `cutting-edge` `state-of-the-art` `game-changing` `groundbreaking` `seamless` `innovative` `nuanced` `intricate` `vibrant` `testament` `landscape` (metaphorical) `realm`

### Banned sentence openers (cut or restructure)
"In today's [world / landscape / era]" · "In the realm of" · "The world of X" · "When it comes to X" · "It's worth noting that" · "It is important to note that" · "It is crucial to understand that" · "It goes without saying that" · "First and foremost" · "Last but not least" · "At the end of the day" · "Moving forward" · "In conclusion, it is clear that"

### Em-dash substitution (zero tolerance)

| Source pattern | Replacement |
|---|---|
| `X — Y` (parenthetical) | `X, Y` or `X (Y)` |
| `X — Y — Z` (nested) | subordinate clause or two sentences |
| `— item` (bullet marker) | standalone sentence |
| `X —` (trailing) | `X,` or close the sentence |

After: clean `,,` → `,` · `:,` → `:` · `,.` → `.`

### Transition word overload
Cut any paragraph-opening transition where the logic is obvious: `Furthermore` `Moreover` `Additionally` `In summary` `To summarize`. Replace with a pronoun or demonstrative: "This explains…" / "That gap…" / "These findings…"

---

## Register Targeting

| Register | Voice | Contractions | Passive | Emotional range |
|---|---|---|---|---|
| `academic` | Argues a position; acknowledges objections; scholarly | sparingly | allowed | Skepticism, irony, intellectual frustration |
| `professional` | Informs and persuades; addresses an intelligent reader | moderate | light | Candor, measured skepticism, direct opinion |
| `casual` | Talks to the reader; admits uncertainty freely | free | rarely | Full range; humor; frustration; enthusiasm |

Default: `professional`.

---

## Workflow

### Phase 0 — Diagnostic inventory (before writing a word)
1. What are the factual anchors? (numbers, names, dates, citations — untouchable)
2. Which of the 4 deep failure modes are worst? (note severity for each)
3. What is the register?
4. Does the intro restate? Does the conclusion summarise? (structural surgery needed)

### Phase 1 — Structural surgery
- Cut or compress restating intro (one sentence max, or delete entirely)
- Cut or compress summarising conclusion (replace with implication or open question)
- Break obvious 5-paragraph template lock
- Identify all 3-part lists → plan to break symmetry

### Phase 2 — Deep Transform pass (section by section)
For each section, apply all four deep transforms:
1. **Specificity**: find every abstraction → inject a concrete anchor
2. **Cognitive trace**: add one mid-thought pivot or self-correction per argumentative paragraph
3. **Rhythm**: read aloud → identify flat stretches → introduce one long+short pair and one fragment or question per section
4. **Asymmetry**: break list symmetry, vary paragraph weight, apply imperfect parallelism

### Phase 3 — Surface elimination sweep
- Zero em-dashes
- Zero banned words
- Zero banned sentence openers
- Zero overloaded transition words at paragraph openings

### Phase 4 — Quality gates (full checklist before delivery)
- [ ] Every abstract claim has a concrete anchor (number, name, date, comparison)
- [ ] At least one cognitive process trace per argumentative paragraph (pivot, doubt, second-guess)
- [ ] No paragraph where all sentences are 15–28 words
- [ ] At least one fragment, question, or short punch (<10 words) per section
- [ ] No list of exactly 3 perfectly parallel items without asymmetry
- [ ] No restating intro; no summarising conclusion
- [ ] Zero em-dashes
- [ ] Zero banned words (run the list, not just the obvious ones)
- [ ] Zero banned sentence openers
- [ ] All factual anchors from source preserved exactly
- [ ] Register consistent throughout

### Phase 5 — Output format
If `.docx` requested, generate a `python-docx` script:
- Calibri 11pt Normal; Heading 1 navy `#1F497D`; Heading 2 blue `#2E74B5`
- Justified body paragraphs; tables with `'Table Grid'` style

If plain text, output markdown.

---

## The Specificity Injection Cheat Sheet

Use these substitution patterns aggressively:

| Abstraction type | What to replace it with |
|---|---|
| Vague quantity | Exact figure or range: "many" → "roughly 60%"; "several" → "four" |
| Vague time | Specific date or period: "recently" → "since Q3 2024" |
| Vague actor | Named person, team, company, institution |
| Generic process | Named step, tool, method: "the system" → "the Redis cache layer" |
| Vague outcome | Measured result: "improved" → "reduced latency from 420ms to 95ms" |
| Abstract quality | Observable behavior: "reliable" → "99.97% uptime over 18 months" |
| Implied comparison | Stated baseline: "better" → "23 points above the benchmark" |

---

## Usage

```
/humanize-ai
```

Paste source text. Optionally specify:
- `--register academic` | `--register professional` (default) | `--register casual`
- `--docx <path>` — Word output
- `--markdown` — markdown output (default)
- `--section "X"` — rewrite one section only

### Examples

```
/humanize-ai --register professional

[paste AI draft]
```

```
/humanize-ai --register academic --docx "C:/Users/.../essay.docx"

[paste AI essay]
```

---

## Research Basis

- **Why surface rewriting fails** — [GPTZero: Detecting AI-Humanized Text](https://gptzero.me/news/detecting-ai-humanized-text-how-gptzero-stays-ahead/) — composite signals survive synonym swaps
- **Specificity as the strongest human signal** — [Hunting the Muse: How to spot AI writing](https://huntingthemuse.net/library/how-to-tell-if-writing-is-ai); [CRAFT Literary: Show Don't Tell and AI](https://www.craftliterary.com/2025/03/26/show-dont-tell-what-ai-cant-do/)
- **Perplexity/burstiness mechanics** — [GPTZero perplexity/burstiness](https://gptzero.me/news/perplexity-and-burstiness-what-is-it/); [Pangram Labs: Why these metrics fail alone](https://www.pangram.com/blog/why-perplexity-and-burstiness-fail-to-detect-ai)
- **Cognitive process authenticity** — [GPTZero: Preserving human writing patterns](https://gptzero.me/news/how-testing-our-own-writing-patterns-is-helping-us-preserve-whats-human/); arxiv 2505.01800 psycholinguistic markers
- **Sentence entropy and structural features** — [Springer AI Review 2024](https://link.springer.com/article/10.1007/s10462-024-10903-2); [PNAS 2025: Do LLMs write like humans?](https://www.pnas.org/doi/10.1073/pnas.2422455122)
- **Metadiscourse deficiency** — [ScienceDirect 2025: Metadiscourse in ChatGPT vs student essays](https://www.sciencedirect.com/science/article/abs/pii/S0889490625000134)
- **Emotional flatness** — [Originality.AI sentiment study](https://originality.ai/blog/study-popular-llms-make-content-neutral-sentiment); arxiv 2509.09593

Sister skill: `/italian-rewriting` — same factual-fidelity rules for academic Italian prose.
