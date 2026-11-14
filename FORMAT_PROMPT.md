# Study guide formatting prompt

A reusable prompt for producing certification study guides in the format of the
NVIDIA NCP-AII guides (`nvidia-ai-infra-guides`) and this repository. Paste it to
an AI assistant, fill in the bracketed parts, and attach the official exam guide.

---

## The prompt

You are writing an interactive study guide for **[CERTIFICATION NAME]**. The
official exam guide is attached (or at [URL]); treat it as the source of truth for
scope, section names and weights. Ground every technical claim in official vendor
documentation.

### Deliverable

One self-contained HTML file, `[topic]-mastery.html`:

- Everything inline: one `<style>` in `<head>`, one `<script>` at the end of
  `<body>`. No CDNs, web fonts, external images, analytics or `fetch` calls.
  Diagrams, if any, are inline `<svg>`.
- Dark pastel theme: background `#1c1b29`, pastel green `#b5e08f` headings,
  pastel blue/peach/lilac/rose/mint accents, dark text on pastel buttons and
  badges, `max-width: 980px` main column. Copy the `<style>` block from an
  existing guide rather than inventing a new look.
- Relative links only between guides (`other-guide.html#section`).

### Page structure (in this order)

1. `<h1>` and a `.subtitle` paragraph: what the guide covers, and what it ends with.
2. `nav.toc.card` with an ordered list linking to every numbered `<h2 id>`.
3. **Exam at a glance**: format, duration, result type, recommended experience,
   then a table of exam sections with weights and "what it really asks". Include
   any renames or version changes learners will meet in older material.
4. **How to answer the questions**: the decision pattern behind the exam's
   scenario questions (for example "least effort that meets every constraint"),
   with a memory hook.
5. **One `<h2>` per exam objective or tightly related group**, labelled with the
   objective number, for example "Serving models (4.1)". Each section has:
   - a short plain-language explanation of what and why;
   - comparison tables ("choose X when…", "not for…");
   - realistic commands, code or config in `<pre><code>`, with comments;
   - one `.key` takeaway, and `.warn` callouts for common wrong answers.
6. **Interactive tools** placed next to the theory they support: calculators,
   builders, decoders or troubleshooters (`div.card > div.tool` of labelled
   inputs, plus a `div.outbox` result that updates on input).
7. **Hands-on labs**: 3–6 short guided exercises (`details.scn`), each with
   numbered steps, "you should be able to say", and a clean-up step. Warn about
   cost where resources bill while idle.
8. **"Which X?" chooser**: buttons; clicking one shows MEANS / WHY / NOT
   (the usual answer, the reason, and the tempting wrong choice).
9. **Sample outputs**: filterable `details.smp` blocks, each with a command,
   realistic output and a "What to look at" paragraph. Mark them illustrative.
10. **Scenarios**: `details.scn` with DIAGNOSE / CAUSE / FIX.
11. **Searchable reference**: `#search` input filtering a two-column `#cheatTable`.
12. **Flashcards**: a `.flash` grid of click-to-flip `.fc` cards.
13. **Common gotchas / exam traps in one list**: an ordered list, one bolded rule
    per item plus a short reason.
14. **Practice quiz**: sticky `#score`, `#quizRoot`, `#resetBtn`. 25–55 original
    questions in the exam's style, each with an explanation.

Number the `<h2>` headings and keep the TOC, heading text and quiz count
("Practice quiz (N questions)") in sync.

### Callout classes (CSS adds the label)

| Class | Label | Use for |
|---|---|---|
| `.key` | Key idea | The one thing to remember from a section |
| `.analogy` | Analogy | A plain-language comparison |
| `.mn` | Memory hook | Mnemonics |
| `.warn` | Exam trap | Common wrong answers and confusions |
| `.note` | Note | Version-specific details and "check your version" hedges |

### Data shapes for the interactive parts

Keep content as data arrays at the top of the script so it's easy to extend:

```js
const picks = [[requirement, useThis, why, notThis], ...];        // chooser
const scenarios = [{ t, diag, cause, fix }, ...];                 // scenarios
const cheat = [[termOrCommand, meaning], ...];                     // reference
const cards = [[front, back], ...];                                // flashcards
const questions = [{ q, opts: [4 strings], a: correctIndex, why }, ...]; // quiz
```

- Spread correct answers across positions 0–3; don't let one index dominate.
- Escape `<` as `&lt;` in HTML and in strings rendered through `innerHTML`.
- Never write `${` inside scripts unless it's real interpolation.

### Writing style

- Write for a learner: define each acronym on first use, use complete sentences,
  and explain *why*, not just *what*.
- Prefer tables for comparisons, `.key` for takeaways, and realistic output for
  anything the learner will see on a real system.
- Hedge version-specific numbers, flags, names and defaults in a `.note` instead
  of stating them as fixed facts. Teach the trade-off the exam tests rather than
  the newest product SKU.
- Use placeholders for anything identifying: `PROJECT_ID`, `BUCKET`, `node001`,
  private example IPs like `10.0.0.11`, `$API_KEY`.

### Content policy

- Never copy exam or practice-test questions verbatim, including their options,
  and never label content with question numbers.
- When a learner shares a question, turn it into an original scenario in your own
  words and explain why each approach is right or wrong.
- Never include real keys, tokens, passwords, hostnames, emails or employer details.

### Validation before publishing

1. Every inline script parses
   (`node -e "new Function(<script contents>)"` for each file).
2. The page loads in a browser with every interactive part rendered: quiz count,
   flashcards, scenarios, reference rows, chooser buttons, calculator output.
3. TOC entries match the `<h2>` ids in order; the quiz count appears in both the
   TOC and the heading.
4. Local links and `#anchors` resolve.
5. Scan for leaks: API key patterns, private keys, `/Users/`, `file://`,
   "Question 12"-style labels.
6. Click through the builders, chooser, flashcards and quiz by hand.
7. Add the guide to `index.html` (a card with a one-line description and an
   exam-value rating) and to `README.md`.
