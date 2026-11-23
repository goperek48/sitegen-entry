# sitegen

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/goperek48/sitegen-entry/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/goperek48/sitegen-entry/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for makefun-site 1.0.0 — a static site generator that returns
byte-identical output to the reference, only faster.

- `solve.js` — the entrypoint. `run(input)` builds one site's output tree.
- `main.ts` — the harness driver: reads `/input/cases.json`, answers each case
  with `run`, writes `/output/answers.json`.

## Speed

The reference spends most of its time rendering Markdown one character at a
time (an HTML-escape regex call per character) and walking template trees
with string concatenation. This entry instead escapes whole plain runs at
once, finds markup with `indexOf` scans, takes an ASCII fast path in the slug
rule, dispatches Markdown blocks on character codes, and accumulates template
output into an array joined once.

## License

MIT — see LICENSE.
