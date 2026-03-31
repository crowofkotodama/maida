# Maida

**You have hundreds of games. Tonight you still don't know what to play.**

You open your Steam library.
You scroll.
You stare.
You close it.
Or you go back to the same few games again—not because they are the best, but because choosing feels heavier than playing.

Maida exists for that moment.

It is not a recommendation engine.
It is not a backlog manager.
It does not try to optimize your library or persuade you to engage more.

Maida shows you **one game at a time** from the games you already have installed.
You answer with a simple choice:
- **Try it now**
- **Not now**

That is enough to begin.

## What problem Maida solves

Maida is built for library paralysis.

When you have 200, 300, or 500 games, the problem is often not access.
It is not a lack of options.
It is that your free time starts to feel like work.

Too many installed games become too many unfinished possibilities.
Instead of excitement, you get hesitation.
Instead of play, you get comparison.
Instead of starting, you close the library and do something else.

Maida reduces that pressure by shrinking the choice itself.

## What Maida is

Maida is a desktop app for Steam players who want a calmer way to begin.

It works like this:
1. It reads the games you already have installed.
2. It presents one game.
3. You decide: now, or not now.
4. Then it gets out of the way.

No endless browsing.
No ranking screen.
No algorithm pretending to know you better than you know yourself.

## What Maida is not

Maida deliberately refuses several common product patterns.

It is **not**:
- a recommendation engine
- a social feed
- a retention trap
- a streak system
- a guilt machine for your backlog

It does not try to keep you inside itself.
If one day you no longer need Maida, that means it worked.

## Core ideas

Maida is shaped around two modes:

- **Kamae** — prepare the field. Narrow the space before choosing.
- **Rin** — face the moment. One game. One decision.

These are not decorative terms. They describe the rhythm of the tool:
prepare quietly, then begin cleanly.

## Accessibility

Accessibility is part of the product, not an afterthought.

Current support includes:
- full keyboard navigation
- NVDA screen reader support on Windows
- gamepad support (D-pad, A/B buttons)
- interface localization in English, Japanese, Simplified Chinese, and Traditional Chinese

## Privacy

Your game data stays on your device.

Maida currently sends **one anonymous ping per launch** containing:
- a random ID
- install day count

This can be turned off in Settings.

## Platform support

- Windows
- Linux

## Development

```bash
pnpm install
pnpm run tauri:dev
```

## Testing

```bash
pnpm run test
pnpm run test:e2e
```

## Building

```bash
pnpm run tauri:build
```

## License

Copyright 2026 Bright Raven World. All rights reserved.
