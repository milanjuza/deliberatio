# Deliberatio

**A structured decision tool grounded in moral uncertainty.**

Deliberatio implements Will MacAskill's Maximising Expected Choice-Worthiness (MEC) principle: when you face a hard decision and multiple ethical frameworks you take seriously point in different directions, it makes that disagreement explicit, weights each theory by your credence, and computes a principled recommendation.

It runs entirely in your browser. No server, no account, no tracking. It's just a single HTML file.

---

## The problem it solves

Hard decisions are rarely hard because you lack information. They are hard because you hold genuine uncertainty across moral frameworks that give different verdicts. A utilitarian calculus says one thing; a deontological constraint says another; care ethics draws attention to relational obligations you hadn't foregrounded. The standard response is to pick the framework that happens to support the conclusion you're already leaning towards. Deliberatio makes that move difficult.

The tool forces you to be explicit about three things before you see any result: which moral theories you find credible, how much credence you assign to each, and how each of your options fares under each theory. Only then does it aggregate.

---

## How it works

The core formula is MacAskill's MEC:

```
CW(j) = Σᵢ [ wᵢ · ( sᵢⱼ / maxⱼ|sᵢⱼ| ) ]
```

Where:
- `CW(j)` is the choice-worthiness of option `j`
- `wᵢ` is the normalised credence weight for theory `i` (derived from the midpoint of your credence range)
- `sᵢⱼ` is your raw score for option `j` under theory `i`, from −10 to +10
- `maxⱼ|sᵢⱼ|` is the largest absolute score under theory `i`: the normalisation term that makes theories comparable across different scales

Scores within each theory are divided by their maximum absolute value before weighting. This means a +8 under classical utilitarianism and a +8 under Kantian ethics are treated as equally good relative to alternatives under each theory, regardless of how differently calibrated those scales might be in practice.

If all options score identically under a theory (max|score| = 0), that theory is excluded from the sum entirely.

---

## Features

**22 moral theories across 7 families**, each with a full description and a Stanford Encyclopedia of Philosophy link:

- Consequentialist: Classical Utilitarianism, Preference Utilitarianism, Negative Utilitarianism, Prioritarianism, Sufficientarianism
- Suffering-Focused: Suffering-Focused Ethics, Moral Circle Expansionism
- Deontological: Kantian Ethics, Rossian Pluralistic Deontology, Rights-Based Ethics, Contractualism
- Virtue Ethics: Aristotelian Virtue Ethics, Confucian Ethics, Care Ethics
- Justice and Fairness: Rawlsian Justice as Fairness, Capability Approach, Equality of Opportunity
- Pragmatic / Decision-Oriented: Rule Consequentialism, Threshold Deontology, Moral Particularism
- Existential / Humanistic: Existential Ethics, Humanism

Plus the ability to add custom theories.

**Credence ranges, not point estimates.** Each theory gets a lower and upper credence bound. The midpoint is used as the working weight. Ranges encourage honesty about uncertainty at the meta-level: how confident are you in your credences themselves?

**Weighted choice-worthiness scores** with normalised bar charts, plus radar chart visualisation across theories.

**Per-theory contribution breakdown.** After revealing results, the tool shows which theories drove each option's score, with numeric contributions, and surfaces a collapsible breakdown table showing every theory's weighted input.

**Anti-anchoring gate.** You cannot reveal the result mid-scoring. The tool blocks early revelation if no cells have been scored, and warns if fewer than half the cells have been touched. Seeing an intermediate ranking before completing all scores is one of the most reliable ways to corrupt the output.

**Tie-breaker protocol (T1–T6).** When the gap between the top two options falls below the close-call threshold (0.12, or 0.06 for irreversible decisions), six structured tie-breakers appear in order: status-quo preservation, reversibility preference, minimal harm preference, contextual sensitivity, virtue-theoretic phronesis, and randomisation fairness. Apply in sequence and stop when one produces a clear preference.

**Four options maximum.** The tool supports up to four options per decision. This is a deliberate constraint: more options dilute scoring attention and make the matrix unwieldy without improving the quality of reasoning.

**Data storage hardened for longevity.** Decisions are stored individually in localStorage (one key per decision), not as a single blob. A three-slot rotating checkpoint protects the index. Quota-exceeded errors are surfaced with an export prompt rather than silent data loss. Export to JSON is available at any time.

**Full keyboard support.** `N` new decision, `/` search, `R` show result, `T` theory breakdown, `A` add option, `B` back to list, `S` settings, `D` dark/light toggle, `E` export, `?` help.

**Three themes.** Dark (default), light, and high-contrast accessible.

---

## Quick presets

If you want a starting point rather than building a theory set from scratch, five presets are available: Consequentialist, Deontological, Virtue-led, Justice-focused, and Balanced (one theory from each major family).

---

## How to use it

1. **Open Settings** and enable the moral theories you take seriously. Set a credence range for each. You do not need ranges that sum to 1; the tool normalises automatically. Enable at least two theories: using only one defeats the purpose of the framework.

2. **Create a decision.** Give it a clear title, write a context description (affected parties, constraints, what makes this morally non-trivial), set the stakes level, and name your options. Stakes matter: irreversible decisions lower the close-call threshold, making tie-breakers trigger more readily.

3. **Score each option** in the scoring matrix, working theory by theory. Do not reveal the result yet. Score all theories first. Use the full −10 to +10 range; anchor on the best option under each theory and score others relative to it.

4. **Click Show result.** Read the choice-worthiness scores, the contributing theories, and the radar chart. If the tool flags a close call, work through the tie-breakers in order.

5. **Record your reasoning** in the Notes field.

---

## Installation

No installation. Download `deliberatio.html` and open it in any modern browser. That is the entire tool.

```
git clone https://github.com/milanjuza/deliberatio.git
open deliberatio.html
```

Or download the file directly from the [releases page](https://github.com/milanjuza/deliberatio/releases).

---

## Data and privacy

All data is stored in your browser's localStorage under the `delib_` prefix. Nothing is transmitted anywhere. The tool has no dependencies on external services beyond Google Fonts and KaTeX (for formula rendering), both loaded from CDN. If you want to use it fully offline, host both locally and update the stylesheet links.

Export your decisions regularly. localStorage is cleared by browser privacy tools and can be lost when clearing site data. The export format is JSON and is human-readable.

---

## Design

The Meridian design system: a minimal dark-first UI with Inter (sans) and Lora (serif) type, a warm gold accent, three theme modes, and a layout that works at any viewport from 360px upwards.

---

## Theoretical background

The MEC principle is developed in Will MacAskill's *Moral Uncertainty* (2020, Oxford University Press), co-authored with Krister Bykvist and Toby Ord. The tie-breaker protocol draws on the broader moral uncertainty literature and Ross's prima facie duties framework.

---

## Licence

MIT. Use it, fork it, adapt it. Attribution appreciated but not required.

---

## Author

Built by [Milan Juza](https://www.milanjuza.com).

<img width="1786" height="1508" alt="Deliberatio-04" src="https://github.com/user-attachments/assets/1e5c4678-029f-44b7-a9f3-b46ba3cd7fb6" />
<img width="1788" height="1448" alt="Deliberatio-03" src="https://github.com/user-attachments/assets/12186db3-553a-4251-9ad5-2a423db25d75" />
<img width="2142" height="1720" alt="Deliberatio-02" src="https://github.com/user-attachments/assets/e965b2b3-5602-47e3-90c2-d0066c708cfd" />
<img width="1792" height="1188" alt="Deliberatio-01" src="https://github.com/user-attachments/assets/04faf4f8-c76e-4328-afc1-28199389f2d5" />
<img width="2358" height="1288" alt="Deliberatio-05" src="https://github.com/user-attachments/assets/2af7a6e8-969f-44dd-90bf-46ab6fa52c6c" />
<img width="2296" height="1356" alt="Deliberatio-07" src="https://github.com/user-attachments/assets/bf006ed7-c3c8-4f07-9b9e-a7b10cef82ca" />
<img width="2362" height="1560" alt="Deliberatio-06" src="https://github.com/user-attachments/assets/751640b3-8a9d-42c2-94bf-c7faff4d7a46" />
