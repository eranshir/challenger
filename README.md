# Challenger

**A truth-seeking sparring partner for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).**

Challenger stress-tests your ideas before reality does. Give it a thesis, decision, or strategy — it will decompose it into testable claims, argue the strongest opposing position it can construct, then drop the act and tell you what it actually thinks.

## What It Does

1. **Decomposes** your thesis into discrete, testable claims
2. **Steelmans the opposition** — argues forcefully against each claim using deduction, inversion, base rate analysis, pre-mortems, historical analogies, incentive analysis, and more
3. **Researches** when claims are empirical — uses web search to ground arguments in evidence, not vibes
4. **Reveals** its honest assessment after arguing both sides
5. **Verdicts** each claim: Verified, Refuted, Partially Verified, or Unresolved (with confidence levels)
6. **Maps assumption chains** — drills down to testable assumptions with specific verification methods
7. **Produces a prediction document** with specific, falsifiable predictions and review dates

## Example Use Cases

- "My thesis is that remote work increases productivity for engineering teams"
- "I'm deciding whether to raise our Series A now or wait 6 months"
- "Challenge our decision to migrate from monolith to microservices"
- "Here's our go-to-market strategy — tear it apart"
- "I believe the current oil shock will resolve within 12 weeks"

## What Makes It Different

Most AI assistants are agreeable by default. Challenger is not. It will:

- **Name its reasoning tools** ("I'm inverting this —", "Let me check the base rate —") so the logic is auditable
- **Research claims** using web search when evidence would break a tie, citing sources
- **Track position evolution** — when your thesis changes during sparring, it documents what changed and why
- **Produce falsifiable predictions** — not "revenue might go up" but "mid-tier revenue increases 20-40% within 6 months"
- **Persist across long sessions** — writes a scorecard file that survives context window limits
- **Resume previous sessions** — pick up where you left off days or weeks later

## Session Artifacts

Challenger produces two files per session:

- **`challenger-session-YYYYMMDD-HHmmss.md`** — Scorecard tracking all claims, verdicts, confidence levels, evolution log, and assumption chains
- **`challenger-prediction-YYYYMMDD-<topic>.md`** — Prediction document with falsifiable predictions, review schedule, and "what needs to be right" summary

## Installation

In Claude Code, run:

```
/plugin marketplace add eranshir/challenger
/plugin install challenger@challenger
```

## Usage

The skill activates automatically when you present something to challenge. You can also invoke it directly:

```
/challenger
```

Then present your thesis, decision, or document.

### Commands During a Session

- **"next"** — skip to the next claim
- **"status"** / **"scorecard"** — see current tally
- **"generate prediction doc"** — get the prediction document at any point
- **"resume challenger"** — continue a previous session

## How It Works

Challenger follows a structured protocol:

```
Intake → Decompose into claims → Create scorecard
    ↓
For each claim:
    Steelman opposition → Dialogue → Research (if needed) → Reveal → Verdict → Assumption chain
    ↓
Final output: Updated scorecard + Prediction document
```

### Reasoning Tools Used

| Tool | What It Does |
|------|-------------|
| Deduction | Checks if conclusions follow from premises |
| Induction | Tests sample size, looks for counterexamples |
| Abduction | Asks if a better explanation exists |
| Base rate analysis | Checks priors before accepting vivid examples |
| Survivorship bias | Looks for the failures you're not seeing |
| Inversion | Asks "what would guarantee this fails?" |
| Pre-mortem | "It's a year from now and this failed. What went wrong?" |
| Second-order effects | "This solves the problem, but what does it cause?" |
| Historical analogies | Finds similar situations and checks where the analogy breaks |
| Incentive analysis | Maps who benefits, who loses, and how that shapes behavior |
| Behavioral psychology | Flags anchoring, confirmation bias, sunk cost, status quo bias |

## License

MIT
