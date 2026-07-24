# Campaign-in-a-Box 📣

**An AI system that turns a one-paragraph brief into a complete, on-brand marketing kit — built and evaluated as a product, not a party trick.**

Most people can get an AI to "write a gym Instagram post". This project is about the
harder, more useful thing: designing a **repeatable system** that reliably produces
*on-brand, audience-targeted, publish-ready* content — and then **measuring** whether
the system actually works.

Built around a fictional independent gym, **Forge Fitness**, but the method is
industry-agnostic: swap the brand voice file, keep the machinery.

> ⚠️ *Forge Fitness is a fictional brand created for this project. All campaigns, URLs,
> and results are illustrative.*

---

## The problem

A small gym has no budget for an agency and no time to write fresh copy for every
promotion. Off-the-shelf AI helps, but out of the box it produces generic, hypey copy
that sounds like every other gym — and can actively repel the nervous first-timers who
are the most valuable audience to win. (See the live example of this failure in
[`evaluation/before-after-comparison.md`](evaluation/before-after-comparison.md).)

## The solution

A three-part system that constrains a general AI model into a consistent brand voice:

1. **A brand brain** — a [brand voice guide](prompts/brand-voice-guide.md) defining
   positioning, three audience personas, and explicit word-level do's and don'ts.
2. **A reusable engine** — a [master system prompt](prompts/01-master-system-prompt.md)
   plus [channel rules](prompts/03-channel-rules.md) that force a planning step,
   ban clichés, and self-check every output.
3. **A simple input** — a [one-paragraph brief template](prompts/02-brief-intake-template.md)
   that makes the *human* decide the two things that matter most: one persona, one action.

Load it once into a Custom GPT or Claude Project, then feed it briefs. Each brief
returns a full kit: 3 social posts, an email, a paid ad, and a flyer concept.

## Does it actually work? (the evaluation)

I scored the system against a naive prompt using a [6-point quality rubric](evaluation/quality-rubric.md).
Same goal, same model, same rubric:

| | Naive prompt ("write me a gym post") | Campaign-in-a-Box |
|---|---|---|
| Quality score | **2 / 12** | **~11.4 / 12** |
| Brand-safety gate | ❌ Hard fail (hype, clichés) | ✅ Pass |
| Publish-ready? | No | Yes |

The naive prompt didn't just score low — it produced "unleash your inner beast" copy
that would scare off the exact beginner the campaign was meant to attract. **The value
is in the system design, not the model.** Full breakdown:
[`before-after-comparison.md`](evaluation/before-after-comparison.md).

## See it in action

Three complete campaigns, each generated from a single brief:

- **[Example 1 — January Fresh Start](examples/example-1-january-fresh-start.md)** —
  free intro offer for nervous first-timers
- **[Example 2 — Express Strength](examples/example-2-express-strength-class.md)** —
  new class launch for time-poor professionals
- **[Example 3 — Welcome Back](examples/example-3-welcome-back.md)** —
  guilt-free win-back for lapsed members

  [Forge_Everyone_Starts.png](https://github.com/carleclan/campaign-in-a-box/blob/main/examples/Forge_Welcome_back.png)

## Repository map

```
campaign-in-a-box/
├── README.md                     ← you are here
├── prompts/                      ← the reusable system
│   ├── brand-voice-guide.md      ← the "brand brain"
│   ├── 01-master-system-prompt.md
│   ├── 02-brief-intake-template.md
│   └── 03-channel-rules.md
├── examples/                     ← 3 full campaigns from 3 briefs
│   ├── example-1-january-fresh-start.md
│   ├── example-2-express-strength-class.md
│   └── example-3-welcome-back.md
├── evaluation/                   ← proof it works
│   ├── quality-rubric.md
│   └── before-after-comparison.md
└── docs/
    └── reflection.md             ← what I learned & what's next
```


