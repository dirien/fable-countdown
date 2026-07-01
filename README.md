# fable-countdown

A split-flap departure board tracking Claude Fable 5's turbulent first month — from launch, through a government grounding, to its redeployment. It now counts down to **July 1, 2026**, when Fable 5 returns to subscription plans.

Live at [fable-countdown.vercel.app](https://fable-countdown.vercel.app).

## The story

Anthropic shipped Fable 5 to Pro, Max, Team, and Enterprise plans on June 9, 2026, free through June 22, after which it would move to usage credits. So I asked Fable to build a countdown to its own departure, and it came up with a Solari-style board: FLIGHT: Claude Fable 5. DESTINATION: Usage credits.

Then the plan fell apart, twice:

- **June 12** — a U.S. export-control directive [suspended](https://www.anthropic.com/news/fable-mythos-access) Fable 5 and Mythos 5 for all customers. The flight was grounded before it left the gate. The board froze and took a red **SUSPENDED** stamp.
- **June 30** — the controls were [lifted](https://www.anthropic.com/news/redeploying-fable-5). The board flipped from Departures to Arrivals, took a green **CLEARED** stamp, and the clock started ticking again.
- **July 1** — Fable 5 returns globally across all platforms, included for up to 50% of weekly usage limits.
- **July 7** — the promotional period ends and usage-credit billing begins.

A new safety classifier now blocks the reported jailbreak in over 99% of cases; the occasional false positive on benign coding falls back to Opus 4.8. Mythos 5 stays limited to approved U.S. organizations.

## How it works

The whole site is one static `index.html`. No build step, no framework, no dependencies beyond the Oswald font from Google Fonts.

The board reads the visitor's own timezone from `Intl.DateTimeFormat().resolvedOptions().timeZone` and runs in three phases off two local-midnight anchors:

1. **Before July 1** — counts down to the return. Green CLEARED stamp, STATUS: Cleared for return.
2. **July 1–7** — Fable 5 is back; the clock counts down the free promo window. STATUS: In service.
3. **After July 7** — STATUS: Usage credits.

Because the anchors are local, someone in Auckland crosses each line before someone in Berlin.

The flap cells are plain CSS: a gradient, a seam across the middle, and a short flutter animation when a digit changes. The stamp is a CSS box distressed with a fractal-noise SVG mask. Both animations are skipped when `prefers-reduced-motion` is set.

## Run it

Open `index.html` in a browser. That's it.

To deploy your own copy:

```bash
vercel deploy --prod
```

## Credit

Made with love by Engin Diri ([X](https://x.com/_ediri), [LinkedIn](https://www.linkedin.com/in/engin-diri/)), with help from the model that keeps changing its own departure time.
