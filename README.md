# Deliberatio

 **Reason through difficult moral decisions under ethical uncertainty.**

Most decision tools assume you've already decided which moral principles are correct. Life is rarely that simple.

Should you tell a painful truth or protect someone's feelings? Donate to the most effective charity or support a cause close to home? Honour a promise or prevent greater harm? Prioritise one person over many? These decisions are difficult not because we lack facts, but because different ethical frameworks often point towards different answers. Deliberatio helps you make those disagreements explicit.

<img width="1792" height="1188" alt="Deliberatio-01" src="https://github.com/user-attachments/assets/04faf4f8-c76e-4328-afc1-28199389f2d5" />

Rather than relying on intuition—or whichever moral theory happens to feel most persuasive in the moment—it lets you evaluate every option across the ethical theories you take seriously, weight those theories according to your confidence in them, and combines them into a transparent recommendation. It doesn't tell you what is morally right. It helps you reason more consistently when you're uncertain which moral principles are right.

Deliberatio runs entirely in your browser as a single HTML file. There is no server, no account, no tracking, and no data ever leaves your computer.

## Why Deliberatio?

Most of us don't consistently reason under moral uncertainty.

Instead, we tend to:

- favour the ethical framework that supports the conclusion we already prefer
- switch between principles without noticing
- overlook why different theories disagree
- treat uncertain moral beliefs as if they were certainties

Deliberatio encourages a different approach.

It asks you to state explicitly:

1. which ethical theories you consider plausible
2. how much confidence you place in each
3. how well each available option performs under every theory

Only then does it aggregate the results.

The process doesn't eliminate moral disagreement—but it makes your reasoning transparent, structured and easier to examine.

# How it works

Using Deliberatio involves four steps.

## 1. Choose your ethical theories

Select the moral theories you consider genuinely plausible. The application includes twenty-two built-in theories across seven major traditions, and you can add your own.

## 2. Assign your credences

Rather than pretending certainty, estimate how much confidence you have in each theory. You specify a lower and upper credence bound. Deliberatio uses the midpoint as the working weight while preserving the range to acknowledge your uncertainty.

## 3. Evaluate your options

Score every available option under every selected theory. Each theory asks a different question.

A utilitarian may prioritise wellbeing.

A Kantian may reject using people merely as means.

A virtue ethicist may ask what a virtuous person would do.

Instead of collapsing these perspectives into a single intuition, Deliberatio keeps them separate until every evaluation has been completed.

<img width="2142" height="1720" alt="Deliberatio-02" src="https://github.com/user-attachments/assets/e965b2b3-5602-47e3-90c2-d0066c708cfd" />

## 4. Review the result

Deliberatio combines your assessments into a single recommendation using Will MacAskill's [Maximising Expected Choice-Worthiness](https://static1.squarespace.com/static/5506078de4b02d88372eee4e/t/5bc7224a0852299b5cd60e86/1539777103255/Why+Maximize+Expected+Choice-Worthiness%3F.pdf) framework.

Alongside the final ranking, you can see:

- the contribution made by every moral theory
- weighted choice-worthiness scores
- radar chart comparisons
- complete scoring breakdowns

Nothing is hidden.

Every recommendation is fully explainable.

# Features

## Moral uncertainty built in

Deliberatio is designed around the idea that you may reasonably assign non-zero confidence to several competing ethical theories simultaneously.

Rather than forcing you to choose one framework, it allows them all to contribute proportionally to the final recommendation.

## Twenty-two built-in ethical theories

The application includes theories from seven major traditions.

### Consequentialist

- Classical Utilitarianism
- Preference Utilitarianism
- Negative Utilitarianism
- Prioritarianism
- Sufficientarianism

### Suffering-focused

- Suffering-Focused Ethics
- Moral Circle Expansionism

### Deontological

- Kantian Ethics
- Rossian Pluralistic Deontology
- Rights-Based Ethics
- Contractualism

### Virtue ethics

- Aristotelian Virtue Ethics
- Confucian Ethics
- Care Ethics

### Justice and fairness

- Rawlsian Justice as Fairness
- Capability Approach
- Equality of Opportunity

### Pragmatic

- Rule Consequentialism
- Threshold Deontology
- Moral Particularism

### Existential and humanistic

- Existential Ethics
- Humanism

Each theory includes a concise explanation together with a link to the relevant Stanford Encyclopedia of Philosophy article.

You can also create entirely custom theories.

## Anti-anchoring workflow

One of the easiest ways to bias a decision is to inspect partial results before you've finished evaluating every option.

Deliberatio deliberately prevents this.

Results remain hidden until meaningful scoring has been completed, reducing the temptation to unconsciously adjust later scores to support an emerging favourite.

<img width="1788" height="1448" alt="Deliberatio-03" src="https://github.com/user-attachments/assets/12186db3-553a-4251-9ad5-2a423db25d75" />


## Transparent recommendations

Every recommendation can be inspected.

See exactly:

- how each theory scored every option
- the weighted contribution from every theory
- overall choice-worthiness
- visual comparisons across theories

The goal is not merely to produce an answer, but to make the reasoning behind it understandable.

## Structured tie-breakers

Some decisions remain genuinely close.

When the difference between the top two options falls below the configured threshold, Deliberatio activates a structured tie-breaking protocol.

The six-stage framework considers:

1. preserving the status quo
2. reversibility
3. minimising potential harm
4. contextual sensitivity
5. practical wisdom (*phronesis*)
6. fair randomisation

Each stage is applied in order until a meaningful preference emerges.

## Local-first by design

Everything happens locally.

- no accounts
- no analytics
- no cloud storage
- no tracking
- no subscriptions

Your decisions remain entirely under your control.

## Robust local storage

Each decision is stored independently rather than inside a single database object.

Additional safeguards include:

- rotating checkpoints
- quota protection
- JSON export
- human-readable backups

## Accessibility

- Full keyboard navigation
- Dark, light and high-contrast themes
- Responsive layout

<img width="1786" height="1508" alt="Deliberatio-04" src="https://github.com/user-attachments/assets/1e5c4678-029f-44b7-a9f3-b46ba3cd7fb6" />

# Example

Imagine you're deciding whether to accept a high-paying job at a company whose products you believe may cause social harm.

A consequentialist may focus on the overall balance of benefits and harms.

A deontologist may consider whether accepting the role violates important duties.

A virtue ethicist may ask what accepting the role says about your character.

Rather than allowing one perspective to dominate by intuition alone, Deliberatio evaluates the decision through each lens before combining them according to your confidence in those theories.

# The mathematics

Deliberatio implements Will MacAskill's **Maximising Expected Choice-Worthiness (MEC)** principle.

For each option:

```
CW(j) = Σᵢ [ wᵢ · ( sᵢⱼ / maxⱼ|sᵢⱼ| ) ]
```

Where:

- **CW(j)** is the final choice-worthiness of option *j*
- **wᵢ** is the normalised credence assigned to theory *i*
- **sᵢⱼ** is the score assigned to option *j* under theory *i*
- scores are normalised within each theory before weighting

Normalisation ensures that different ethical theories contribute proportionally even if their internal scoring scales differ.

# Quick start

1. Select the ethical theories you consider plausible.
2. Assign credence ranges.
3. Create a decision.
4. Score every option under every theory.
5. Reveal the result.
6. Review the explanation.
7. Record your reasoning.

# Installation

No installation is required.

Simply download `deliberatio.html` directly from release page.

# Privacy

Deliberatio stores all data locally using your browser's `localStorage`.

Nothing is transmitted anywhere.

No information leaves your computer.

Regular JSON exports are recommended, as browser storage may be cleared by privacy tools or browser settings.

# Theoretical background

Deliberatio is inspired by the framework developed in:

> Will MacAskill, Krister Bykvist & Toby Ord,
> *Moral Uncertainty*
> Oxford University Press (2020)

Its recommendation engine implements the principle of **Maximising Expected Choice-Worthiness**, allowing decisions to reflect uncertainty across competing moral theories rather than assuming any single framework is certainly correct.

## Licence

Free for personal use.

## Author

Built by [Milan Juza](https://www.milanjuza.com).

<img width="2358" height="1288" alt="Deliberatio-05" src="https://github.com/user-attachments/assets/2af7a6e8-969f-44dd-90bf-46ab6fa52c6c" />
<img width="2296" height="1356" alt="Deliberatio-07" src="https://github.com/user-attachments/assets/bf006ed7-c3c8-4f07-9b9e-a7b10cef82ca" />
<img width="2362" height="1560" alt="Deliberatio-06" src="https://github.com/user-attachments/assets/751640b3-8a9d-42c2-94bf-c7faff4d7a46" />
