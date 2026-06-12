# fable-countdown

A split-flap departure board counting down the days until Anthropic removes Claude Fable 5 from subscription plans on June 23, 2026.

Live at [fable-countdown.vercel.app](https://fable-countdown.vercel.app).

## The story

Anthropic shipped Fable 5 to Pro, Max, Team, and Enterprise plans on June 9, 2026, free through June 22. From June 23 it needs usage credits, until there is enough capacity to bring it back to subscriptions. See the [announcement](https://www.anthropic.com/news/claude-fable-5-mythos-5).

So I asked Fable to build a countdown to its own departure. This is what it came up with: a Solari-style departure board. FLIGHT: Claude Fable 5. DESTINATION: Usage credits. STATUS: On time, until it isn't.

## How it works

The whole site is one static `index.html`. No build step, no framework, no dependencies beyond the Oswald font from Google Fonts.

The counter is anchored to midnight on June 23 in the visitor's own timezone, taken from `Intl.DateTimeFormat().resolvedOptions().timeZone`. Someone in Auckland sees one day less than someone in Berlin, because for them June 23 arrives earlier. Once it does, the board flips to DEPARTED.

The flap cells are plain CSS: a gradient, a seam across the middle, and a short flutter animation when a digit changes. The animation is skipped when `prefers-reduced-motion` is set.

## Run it

Open `index.html` in a browser. That's it.

To deploy your own copy:

```bash
vercel deploy --prod
```

## Credit

Made with love by Engin Diri ([X](https://x.com/_ediri), [LinkedIn](https://www.linkedin.com/in/engin-diri/)), with help from the departing model itself.
