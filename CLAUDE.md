# PRISM

A visual render instrument: an audio-reactive render engine shipped as a static
GitHub Pages build. `index.html` is a thin shell that iframes `prism.html`;
the app's JS, CSS and fonts live in `assets/` with hashed names. There is no
source tree or build step in this repo. Treat `assets/` as build output.

## Design stack

Prism's design language is fixed in `assets/prism-style-*.css` under `:root`.
Read it before inventing anything. The rules it encodes:

- Near-black ground (`--bg #07080b`), translucent white surface steps, no grays.
- Square. Every Prism part is `border-radius: 0`.
- Space Grotesk for UI, IBM Plex Mono for values. Both ship as woff2 in `assets/`.
- Controls are silver (`--accent #d4d6dc`) with a machined face: grain,
  edge light, chromatic fringe. Hue is reserved for signal: `--prism #ff6600`,
  `--heat`, `--flare`, `--phos #54e0ff`.
- Section labels are 11px, bold, uppercase, tracked 0.14em.

### Stageshow: faux UI of Prism

Source: [benji.org/stageshow](https://benji.org/stageshow), added to Drew's
Are.na Resources channel on 2026-10-31. MIT, by Benji Taylor.

Use Stageshow whenever the job is an illustration *of* Prism rather than Prism
itself: landing and OG imagery, launch posts, feature cards, a looping hero of
someone picking a Look, a bento of the Lab panels, a docs diagram of the audio
path. Don't hand-roll mock windows or cursors for these.

Install it for the session (pinned to the commit this repo's look was built against):

```sh
npx skills add benjitaylor/skills --skill stageshow
# reviewed at benjitaylor/skills@8020574
```

Then follow its seven-step workflow. Prism-specific decisions:

1. **Look.** Always `theme="dark"`, `palette="accent"`, and
   `className="look-prism"` with `design/stageshow/prism.css` loaded after the
   kit's `stageshow.css`. That file maps Prism's real tokens onto the kit's.
   If Prism's `:root` changes, update the mapping from the stylesheet.
2. **One lit colour.** `--ss-accent` is prism orange. Spend it on the single
   thing the story is about. Everything else stays silver and white.
3. **The canvas is not faux.** Stageshow can't draw, and Prism's output is the
   product. The render area in any demo is a real capture from Prism (a still
   or a short loop exported from the app) dropped into the stage. Only the
   chrome around it (Looks gallery, Lab panels, tabs, transport) is built with the kit.
4. **Real words.** Prism's vocabulary is the content: Looks, Lab, Signal,
   halftone, bayer, stipple, ascii, phosphor. Placeholder lines for the rest.
5. **Closest gold examples.** `dark-hero` (depth from surface steps on black,
   one lit colour) for a hero. `dark-bento` or `ruled-bento` for a grid.
   `panel-annotation` for "this knob changed that render". `chart-scrub` for
   anything audio-reactive scrubbing a value.
6. **Rehearse.** Film it with Stageshow's `film.mjs`, then put the still next to
   a real Prism screenshot at the same scale. Accent, grey temperature, square
   corners and type must match at a glance.
