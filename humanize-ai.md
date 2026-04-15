---
name: humanize-ai
description: Rewrite AI-generated English text into natural human prose by correcting the nine documented failure modes of LLM writing — metadiscourse deficiency, sentence entropy collapse, lexical uniformity, emotional flatness, cohesive device overload, syntactic heaviness, interactional vacuum, template lock, and predictable word choice — while preserving every fact exactly.
level: 3
---

# Humanize AI

Rewrite AI-generated English text into fluent, natural prose grounded in linguistic research. Preserves every fact, number, citation, and structural claim exactly — changes only the language surface. Corrects all nine documented failure modes that make LLM text detectable, and replaces them with register-appropriate, idiomatic English.

## When to Use

- user provides text, a PDF extract, docx content, or a draft and says "make it sound human", "humanize this", "remove AI tone", "fix the AI writing"
- source was clearly written by an LLM (em-dashes, "delve into", every paragraph opening with "Furthermore", uniform sentence lengths)
- output needs to pass a specific register: academic paper, professional report, casual prose

Do **not** use when:
- user wants a translation, not a rewrite
- source is already natural, polished English
- user explicitly wants structured LLM-style output preserved

---

## The Science: Why AI Text Is Detectable

Research across computational linguistics, corpus analysis, and NLP (2023–2025) identifies nine structural failure modes in LLM output. Each has a specific correction technique.

---

### Failure Mode 1 — Low Perplexity + Low Burstiness

**What it is:** Language models choose statistically probable tokens. The result is text with uniformly low surprise value — every word is the expected word. *Burstiness* measures variation in that surprise across a document. Human writing has spikes (unexpected metaphors, sudden short sentences, idiomatic turns) followed by predictable stretches. LLM text is flat throughout.

**What it looks like:** Every clause reads smoothly. No jarring phrase. No sentence that makes you pause. Rhythmically even.

**Fix:** Deliberately insert high-perplexity moments:
- Replace a predictable word with a precise but unexpected synonym
- Use a domain-specific term where a generic one was used
- Drop an idiomatic phrase where the LLM used a literal description
- Write one short, punchy sentence that "shouldn't" be there by standard structure rules

---

### Failure Mode 2 — Sentence Length Entropy Collapse

**What it is:** Research (Springer Nature, 2024) shows human writing follows a scattered, near-power-law sentence length distribution — many short sentences (3–8 words), a few very long ones (40+), and everything in between. LLM output clusters tightly around 18–25 words per sentence regardless of content.

**What it looks like:** Every sentence is approximately the same length. The paragraph has a mechanical, even cadence.

**Fix — mandatory sentence length audit on every paragraph:**
- After any paragraph where all sentences fall between 15–28 words, rewrite at least one to under 10 words and one to over 35 words
- Fragments are legal in professional and casual registers: "Not always." "Here's the problem."
- Starting sentences with conjunctions is human: "But this assumes…", "And yet…", "So what?"
- Never start three consecutive sentences with the same grammatical structure (subject + verb + object × 3)

---

### Failure Mode 3 — Dependency Tree Imbalance

**What it is:** Humans naturally practice dependency length minimization (DLM) — a cognitive optimization that places related words close together to reduce working-memory load. Human dependency parse trees tend to have balanced left/right subtrees and shorter constituent depths. LLM output produces longer, unbalanced subtrees that feel grammatically correct but cognitively heavy.

**What it looks like:** Long noun phrases stacked before the verb. Multiple embedded clauses. Nominalizations instead of verbs. "The implementation of the process of optimization of resource allocation" instead of "optimizing how resources are allocated."

**Fix — denominalize and balance:**
- Convert nominalizations back to verbs wherever natural: `the utilization of` → `using`; `the implementation of` → `implementing`; `the provision of` → `providing`
- Move the main verb earlier in the sentence
- Split any clause that requires re-reading to parse
- Prefer: short subject → short verb → object. Reserve complexity for the clause that deserves emphasis.

---

### Failure Mode 4 — Metadiscourse Deficiency

**What it is:** Academic corpus research (ScienceDirect, 2025) identifies three classes of interactional metadiscourse that AI text systematically underuses:

| Class | Function | Examples |
|---|---|---|
| **Hedges** | Signal uncertainty, epistemic modesty | *probably, might, seems, appears, suggests, arguably, in most cases* |
| **Boosters** | Signal conviction, emphasis | *certainly, clearly, indeed, in fact, without doubt, never, always* |
| **Attitude markers** | Signal writer's stance/emotion toward content | *unfortunately, remarkably, surprisingly, crucially, understandably* |

AI text is "structurally proficient but rhetorically detached" — it organizes information but doesn't take positions or signal uncertainty. The result reads like a Wikipedia article written by a committee.

A fourth class is also missing:

| Class | Function | Examples |
|---|---|---|
| **Engagement markers** | Address the reader, create dialogue | *consider, note that, as we know, you might wonder, imagine* |

**Fix:**
- Add at least one hedge per argumentative paragraph: "This likely explains…" not "This explains…"
- Add at least one booster where the claim is strong: "This is clearly not…" not "This is not…"
- Add attitude markers to flag the writer's stance: "Remarkably, none of these approaches…"
- Add one engagement marker per section: "Consider what this means in practice." / "Note that this does not apply to…"

---

### Failure Mode 5 — Emotional Flatness and Positive Bias

**What it is:** RLHF training optimizes LLMs for agreeableness and positivity. Research (Originality.AI, 2024; arxiv 2509.09593) shows LLMs systematically produce more positive, less negative sentiment than humans. They flatten negative emotional content, avoid expressing doubt, frustration, skepticism, or irony, and gravitate toward motivational register. Human writing carries negative emotions (fear, doubt, frustration, irony) as naturally as positive ones.

**What it looks like:** Conclusions that always resolve optimistically. Objections acknowledged but immediately neutralized. No genuine uncertainty. Every limitation "presents an opportunity."

**Fix — emotional range restoration:**
- If the source content is genuinely ambiguous or problematic, say so: "This remains unsettled." "The evidence here is thin."
- Allow a sentence to end without resolution: "Whether this holds in practice is unclear."
- Use irony or understatement where appropriate: "Calling this a minor complication may be generous."
- Express negative register where the content calls for it: "Unfortunately," "The problem is acute," "This is a significant failure"
- Do not convert a limitation into an opportunity unless the source does so explicitly

---

### Failure Mode 6 — Lexical Diversity Collapse

**What it is:** Research on type-token ratio (TTR) shows LLMs, especially GPT-3.5, have measurably lower lexical diversity than humans. GPT-4 is closer to human TTR overall but collapses in genre-specific vocabulary where training data is sparse. Key finding: Gemini and similar models overuse stopwords and repeated phrases, producing formulaic rhetorical texture.

**What it looks like:** The same word appears three times in a paragraph. Vague words (things, aspects, factors, elements, areas) substitute for precise ones. The vocabulary feels "school report" generic.

**Fix:**
- Check every paragraph for word repetition: same root word appearing twice → replace one instance with a synonym or restructure
- Replace generic words with precise ones: `aspects` → name the aspect; `elements` → name the element; `things` → name the things
- Vary the verbs: if a paragraph uses "shows" three times, replace two with "indicates", "reveals", "demonstrates", "confirms", "suggests"
- Add one domain-specific term per section that earns its place

---

### Failure Mode 7 — Cohesive Device Overload

**What it is:** LLMs achieve text coherence through explicit connective devices — "Furthermore", "Moreover", "Additionally", "In conclusion", "It is worth noting that" — because they process each sentence somewhat independently and signal transitions explicitly. Human writers achieve cohesion through pronoun reference, semantic continuity, and logical implication. They use explicit connectives sparingly, only where the logical jump is genuinely large.

**What it looks like:** Every paragraph opens with a transition word. "In conclusion" before a final paragraph. "It is important to note that" before a routine fact. "Moving forward" before a normal continuation.

**Fix:**
- Delete any transition word at the start of a paragraph where the logic is self-evident from what came before
- Replace "Furthermore, X also Y" → "X also Y" — the fact that it's additional is clear
- Replace "In conclusion, it is clear that…" → start the conclusion directly with its claim
- Reserve explicit connectives for genuine logical pivots (contrast, concession, strong causation)
- Use pronouns and demonstratives to carry cohesion: "This explains…", "These findings suggest…", "That gap is significant."

**Banned explicit transitions (context-dependent — cut when logic is clear):**
`Furthermore` `Moreover` `Additionally` `In conclusion` `In summary` `To summarize` `It is worth noting that` `It is important to note that` `It is crucial to understand that` `Moving forward` `First and foremost` `Last but not least` `At the end of the day`

---

### Failure Mode 8 — Interactional Vacuum

**What it is:** LLMs write as if broadcasting to no one. Human writers — even in formal academic prose — construct an implied reader, anticipate objections, acknowledge competing views, and build a writer-reader relationship. The absence of this makes AI text feel like reference material rather than an argument.

**What it looks like:** No questions. No acknowledgment of objections. No "one might argue…". No reader address. Passive constructions that hide the agent. "It has been argued that…" with no sense of who argued it or whether the author agrees.

**Fix:**
- Add at least one anticipatory acknowledgment per argumentative section: "One might object that…" / "This does not mean that…" / "The obvious question is…"
- Use the first person or second person at least once per major section (register-dependent)
- Name the opposing position before dismissing it: don't just assert your claim, acknowledge what it displaces
- Use rhetorical questions sparingly but deliberately: "But does this actually hold?"
- In academic register: acknowledge the limit of your own argument explicitly at least once

---

### Failure Mode 9 — Five-Paragraph Template Lock

**What it is:** LLMs default to a rigid essay scaffold: (1) introductory paragraph restates the prompt/question, (2) three body paragraphs each with a topic sentence and transition, (3) conclusion paragraph that summarises what was just said. This structure is so deeply embedded from training data that it appears even when explicitly told not to use it.

**What it looks like:** The first paragraph explains what the text is going to say. The last paragraph says what was just said. Every body paragraph has a one-sentence opener followed by exactly two or three supporting sentences.

**Fix:**
- Cut or compress the intro if it only restates the question — start with the answer or the most important claim
- Cut or compress the conclusion if it only summarises — end with an implication, an open question, or a consequence
- Break paragraph length uniformity: some paragraphs can be one sentence; some can run eight sentences
- Start at least one section mid-thought or with a concrete example before the abstract claim

---

## Banned AI Word List

These words are statistically overrepresented in LLM output across multiple corpora. Replace every instance.

**Verbs:** `delve` `leverage` (as synonym for "use") `navigate` `explore` `unlock` `transform` `foster` `underscore` `streamline` `empower` `harness`

**Adjectives:** `pivotal` `crucial` `comprehensive` `multifaceted` `robust` `paramount` `cutting-edge` `state-of-the-art` `game-changing` `groundbreaking` `seamless` `innovative` `nuanced` `intricate` `vibrant`

**Nouns/phrases:** `testament` (as in "a testament to") `landscape` (as in "in today's landscape") `realm` (as in "in the realm of")

**Filler sentence openers** (cut or restructure):
- "In today's [world / landscape / era / fast-paced environment]"
- "In the realm of X"
- "The world of X"
- "When it comes to X"
- "It's worth noting that"
- "It is important to note that"
- "It is crucial to understand that"
- "It goes without saying that"
- "First and foremost"
- "Last but not least"
- "At the end of the day"
- "Moving forward"
- "In conclusion, it is clear that"

---

## Register Targeting

The skill supports three registers. Specify with `--register`. Default is **professional**.

| Register | Sentence style | Contractions | Passive | Hedging | Emotional range |
|---|---|---|---|---|---|
| `academic` | complex; subordinate clauses OK | sparingly | allowed; "has been documented" | formal: "evidence suggests", "it appears that" | Irony and critique; scholarly distance |
| `professional` | crisp; short + medium mix | moderate (don't, it's, we've) | light; prefer active | measured: "likely", "typically" | Measured skepticism; acknowledge problems |
| `casual` | short sentences; conversational | free | rarely | light: "probably", "I'd say" | Full range including frustration/humor |

---

## Em-Dash Substitution

Em-dashes (—) are the single most visible AI fingerprint in English. Zero tolerance.

| Source pattern | Replacement |
|---|---|
| `X — Y` (parenthetical) | `X, Y` or `X (Y)` or subordinate clause |
| `X — Y — Z` (nested aside) | rephrase as subordinate clause or split sentences |
| `— item` (bullet marker) | standalone sentence |
| `X —` (trailing) | `X,` or close the sentence |
| `which — by definition —` | `which, by definition,` |

After substitution: clean `,,` → `,` · `: ,` → `:` · `,.` → `.` · `,;` → `;`

---

## Workflow

### Step 0 — Diagnose the source
Before writing a word, run a full diagnostic pass:

1. **Failure mode inventory**: which of the 9 modes are present? (sentence length check, em-dash count, metadiscourse scan, banned word list, template structure check)
2. **Factual anchors**: list every number, citation, proper noun, percentage, date — these are untouchable
3. **Register**: confirm target (ask if not specified)
4. **Structural map**: what are the sections? Does the intro just restate? Does the conclusion just summarise?

### Step 1 — Structural surgery (Failure Modes 8 & 9)
Fix the architecture first, before touching sentences:
- If intro only restates, cut or compress to one sentence maximum
- If conclusion only summarises, cut to implication/consequence
- Identify paragraphs with template-lock structure and note which ones need a depth or length intervention

### Step 2 — Sentence-level rewrite (Failure Modes 1, 2, 3, 6)
Section by section:
1. Audit sentence lengths — introduce short and long outliers in every paragraph
2. Denominalize: convert noun-heavy phrases to verbal constructions
3. Replace banned words from the full list
4. Improve lexical diversity: check for word repetition, replace with precise synonyms
5. Insert one high-perplexity moment per section (unexpected but apt word choice)

### Step 3 — Rhetorical restoration (Failure Modes 4, 5, 7, 8)
Layer in the human rhetorical texture:
1. Add hedges, boosters, attitude markers (at least one each per argumentative section)
2. Add one engagement marker per section
3. Restore emotional range where the content calls for it — do not neutralize problems
4. Delete explicit transitions where logic is self-evident; replace with pronouns/demonstratives
5. Add one anticipatory acknowledgment of objection per argumentative section

### Step 4 — Post-process sweep
- [ ] Em-dash count = 0
- [ ] Every number/citation matches source exactly
- [ ] Zero banned words from the AI word list
- [ ] Zero banned filler openers
- [ ] Sentence lengths vary within every paragraph (no paragraph where all sentences are 15–28 words)
- [ ] At least one hedge and one booster per argumentative section
- [ ] No paragraph opening with a banned transition word
- [ ] No intro that only restates; no conclusion that only summarises
- [ ] Register consistent throughout (no tonal breaks)

### Step 5 — Output format
If writing to a Word document (.docx), generate a Python script using `python-docx` that:
- Uses Calibri 11pt Normal style
- Uses Heading 1 (navy `#1F497D`) for h1, Heading 2 (blue `#2E74B5`) for h2
- Justifies all body paragraphs
- Adds tables with `'Table Grid'` style
- Outputs to the user-specified path

If writing to plain text, output raw markdown.

---

## Connectives Palette (use sparingly — only at genuine logical pivots)

**Contrast:** however, yet, that said, even so, by contrast, on the other hand, while this is true  
**Addition:** also, in addition, beyond this, a further consideration is, equally relevant  
**Cause/Effect:** therefore, as a result, consequently, it follows that, this explains  
**Sequence:** first, then, next, after that, finally, subsequently  
**Example:** for instance, for example, to illustrate, consider the case of  
**Concession:** although, even though, granted, admittedly, while it is true that  
**Emphasis (use as boosters):** indeed, in fact, notably, above all, what matters here is  
**Summary (use only once, at true end):** in short, in sum, taken together, on balance  

---

## Quality Gates

Before delivering output:

1. **Factual accuracy** — spot-check 5 random facts against source; zero invention
2. **Em-dash count** — search for `—`; must be zero
3. **Banned word scan** — search top 15: `delve` `leverage` `pivotal` `crucial` `comprehensive` `seamless` `robust` `foster` `underscore` `testament` `nuanced` `landscape` `realm` `streamline` `game-changing`
4. **Filler opener scan** — check every paragraph's first sentence; none may begin with a banned phrase
5. **Sentence entropy check** — any paragraph where all sentences are 15–28 words must be revised
6. **Metadiscourse check** — at least one hedge, one booster, one attitude marker per argumentative section
7. **Emotional register check** — no problem neutralized into an opportunity unless source does so; skepticism allowed
8. **Template check** — intro does not merely restate; conclusion does not merely summarise
9. **Register consistency** — no tonal breaks throughout

---

## Usage

```
/humanize-ai
```

Then paste or attach the source material. Optionally specify:
- `--register academic` | `--register professional` (default) | `--register casual`
- `--docx <path>` — output as .docx file
- `--markdown` — output as markdown (default)
- `--section "X"` — rewrite only a named section

### Example invocations

```
/humanize-ai --register academic

[paste LLM-generated essay extract]
```

```
/humanize-ai --register casual --markdown

[paste blog post that sounds robotic]
```

```
/humanize-ai --register professional --docx "C:/Users/.../report.docx"

[paste executive summary with heavy AI tone]
```

---

## Research Basis

This skill is grounded in the following research streams (2023–2025):

- **Perplexity/burstiness as detection features** — GPTZero, Pangram Labs, EMNLP 2023 CT² paper
- **Sentence length entropy** — Springer AI Review (2024): *Contrasting Linguistic Patterns in Human and LLM-Generated News Text*
- **Dependency length minimization** — Nature Human Behaviour (2025): *Active use of latent tree-structured sentence representation*; linguistic DLM theory (widely documented cross-linguistically)
- **Metadiscourse deficiency** — ScienceDirect (2025): *Rhetorical distinctions: Comparing metadiscourse in essays by ChatGPT and students*; corpus-based interactional metadiscourse analysis (~1.3M words)
- **Emotional flatness / positive bias** — Originality.AI study; arxiv 2509.09593 *Fluent but Unfeeling*; PNAS (2025): *Do LLMs write like humans?*
- **Lexical diversity (TTR)** — ScienceDirect (2024): *Playing with words: Comparing vocabulary and lexical diversity of ChatGPT and humans*; Frontiers in Education (2025)
- **Cohesive device overload** — PMC (2025): *A linguistic comparison between human- and AI-generated content*
- **Interactional vacuum** — ResearchGate: *How AI Constructs Stance*; Springer Language Testing in Asia (2024)

Sister skill: `/italian-rewriting` — same factual-fidelity and em-dash rules applied to academic Italian prose.
