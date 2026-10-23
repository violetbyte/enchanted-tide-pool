# My Enchanted Tide Pool

A cozy habit planner with an animated pixel-art tide pool. Check things off your list and a snack drifts down for the fish.

**Live demo:** https://enchanted-tide-pool.vercel.app/

<!-- Add a screenshot or short screen recording here, e.g.:
![My Enchanted Tide Pool](docs/screenshot.png)
-->

The whole app is one file, `index.html`. It uses plain HTML, CSS and JavaScript, with no framework, no build step and no backend.

## Features

**Planner**
- Add habits or one-off tasks with an optional category (Health, Work, Mind, Movement).
- Mark items as daily (they come back fresh each morning) or just once.
- Flag items as a Quick win or Important (star).
- A "What should I do next?" card suggests one task and says why. "Suggest another" steps through the rest.
- A collapsible Completed Today section, a task count, and a time-of-day greeting.
- Removing an item can be undone for a few seconds.

**Tide pool**
- Six pixel-art fish drawn on canvas from character grids, each with its own look and movement quirks (pausing, wiggling, darting).
- Finishing a task drops a snack, and the nearest fish swims over to eat it with a sparkle burst.
- Bubbles, light rays, swaying seaweed, and ambient sparkles.
- Hover, focus or tap a fish to see its name and a one-line description.
- A "Pause motion" button freezes all movement. Snacks still appear when paused.

## Design decisions

- **Gentle by design.** There are no streaks, no failure states, and nothing that punishes missed tasks. Unfinished items simply wait on the list.
- **Day rollover is derived, not destructive.** Whether an item is "done today" is computed by comparing its last-completed date with today's local date. Nothing is deleted at midnight. Finished one-off tasks are hidden, not erased.
- **Works without a backend.** Data is saved in the browser's `localStorage`. If storage is blocked, the app falls back to in-memory state instead of failing.
- **Accessibility.** The app is usable with a keyboard, has visible focus rings, uses toggle buttons with `aria-pressed`, announces status messages through a live region, and respects `prefers-reduced-motion` (it starts paused).
- **No image assets.** All fish, coral, shells and the logo are rendered from small character maps onto canvas, so there are no sprite files to host.

## Run it locally

No install is needed. Open `index.html` in a browser.

To serve it over HTTP instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

It is a static site, so any static host works. I deploy it on [Vercel](https://vercel.com): import the repository, leave the framework preset as "Other", leave the build command empty, and deploy.

## Known limitations

- Data lives in one browser on one device. There is no sync and no account.
- Headings use Google Fonts (Pixelify Sans and Nunito). Offline, or if the fonts fail to load, the page falls back to system fonts.
- There is no automated test suite. I tested it by hand: add, complete, undo, remove, refresh, a simulated date change, pause, and keyboard-only use.

## Tech

HTML5, CSS3, vanilla JavaScript, Canvas 2D, `localStorage`.

## License

[MIT](LICENSE)
