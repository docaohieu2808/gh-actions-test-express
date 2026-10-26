# gh-actions-test-express

[![CI](https://github.com/docaohieu2808/gh-actions-test-express/actions/workflows/ci.yml/badge.svg)](https://github.com/docaohieu2808/gh-actions-test-express/actions/workflows/ci.yml)

Level 1.5 of the GitHub Actions track: a copy of [expressjs/express](https://github.com/expressjs/express) (MIT,
original copyright and history kept; Express's own readme is in [EXPRESS-README.md](EXPRESS-README.md)) used as a
real-world project for [reusable-workflows](https://github.com/docaohieu2808/reusable-workflows).

A toy project only proves the pipeline runs. Express proves it copes with a real one: hundreds of mocha tests, ESLint,
and a large dependency tree. CI is one call to the reusable pipeline, pinned to its v2.0.1 commit:

```yaml
jobs:
  pipeline:
    uses: docaohieu2808/reusable-workflows/.github/workflows/auto-pipeline.yml@879b76e3e519725f0bfaea657865182b72addf4f # v2.0.1
```

The pipeline detects Node, installs from the committed `package-lock.json` (`npm ci`), runs `npm run lint` and
`npm test`, and scans dependencies (Trivy) and the tree for secrets (gitleaks). It runs on every push, on pull
requests and every Monday.

The repository also keeps Express's own SHA-pinned CodeQL and OpenSSF Scorecard workflows, a useful comparison with
how a mature project hardens its supply chain.

Track: `test-gh-actions` (L1) → `gh-actions-test-express` (L1.5) → `reusable-workflows` (L5–6).

Run locally: `npm ci && npm run lint && npm test`.
