# humanize-ai — Claude Code Skill

A Claude Code skill that rewrites AI-generated English text into natural, human-sounding prose.  
Drop-in counterpart to [`italian-rewriting`](https://github.com/enrico1c/italian-rewriting) — same factual-fidelity and em-dash rules, applied to English across three registers.

---

## What it does

Paste any LLM-generated text and get back prose that:

- Has **zero em-dashes** (the #1 AI fingerprint in English)
- Contains **none of the banned AI words** — no `delve`, `leverage`, `pivotal`, `seamless`, `robust`, `testament`, `underscore`, `foster`, `nuanced`, `comprehensive`, `multifaceted`, `cutting-edge`
- Has **no filler openers** — no "In today's world", "It's worth noting that", "It is important to note"
- Uses **varied sentence lengths** instead of the LLM's uniform ~20-word cadence
- Matches your **target register** — academic, professional, or casual
- Preserves **every fact, number, citation, and proper noun** exactly as in the source

---

## Install

Copy `humanize-ai.md` to your Claude Code skills directory:

```bash
# macOS / Linux
cp humanize-ai.md ~/.claude/skills/humanize-ai.md

# Windows (Git Bash / PowerShell)
cp humanize-ai.md $env:USERPROFILE\.claude\skills\humanize-ai.md
```

Claude Code picks up skill files from `~/.claude/skills/` automatically — no restart needed.

---

## Usage

```
/humanize-ai
```

Then paste your source text. Supported flags:

| Flag | Values | Default |
|---|---|---|
| `--register` | `academic` \| `professional` \| `casual` | `professional` |
| `--docx <path>` | path to output .docx file | — |
| `--markdown` | plain markdown output | ✓ (default) |
| `--section "X"` | rewrite only a named section | — |

### Examples

```
/humanize-ai --register academic

[paste LLM-generated essay section here]
```

```
/humanize-ai --register casual --markdown

[paste blog post draft that sounds robotic]
```

```
/humanize-ai --register professional --docx "C:/Users/me/report.docx"

[paste executive summary]
```

---

## Core rules (quick reference)

### Banned AI words
> `delve` `leverage` `navigate` `explore` `unlock` `transform` `pivotal` `crucial` `comprehensive` `multifaceted` `robust` `streamline` `paramount` `cutting-edge` `state-of-the-art` `game-changing` `groundbreaking` `seamless` `innovative` `empowering` `nuanced` `intricate` `vibrant` `foster` `underscore` `testament`

### Banned filler openers
> "It's worth noting that" · "It is important to note that" · "In today's world / landscape / era" · "In the realm of" · "The world of X" · "First and foremost" · "Moving forward" · "In conclusion, it is clear that"

### Em-dash substitution
| Source | Replacement |
|---|---|
| `X — Y` (parenthetical) | `X, Y` or `X (Y)` |
| `X — Y — Z` (nested aside) | subordinate clause or two sentences |
| `— item` (bullet marker) | standalone sentence |
| `X —` (trailing) | `X,` or close sentence |

### Register targets

| Register | Contractions | Passive | Hedging |
|---|---|---|---|
| `academic` | sparingly | allowed | "evidence suggests", "it appears that" |
| `professional` | moderate | light | "likely", "typically" |
| `casual` | free | rarely | "probably", "I'd say" |

---

## Quality gates (checklist)

Before delivering output, verify:
- [ ] `—` count = 0
- [ ] No banned words in the text
- [ ] No filler openers in any paragraph
- [ ] Sentence lengths vary within each paragraph
- [ ] Every fact/number matches the source exactly
- [ ] Register is consistent throughout

---

## Sister skill

[`italian-rewriting`](https://github.com/enrico1c/italian-rewriting) — same approach for academic Italian prose (university papers, thesis chapters), with full accent rules and Italian punctuation norms.

---

## License

MIT
