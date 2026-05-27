<p align="center">
  <img src=".github/profile/wordmark.svg" alt="Macrokit" width="320">
</p>

<p align="center">
  <strong>An open-source SDK that lets weak and local LLMs work like frontier models on narrow workflows.</strong>
</p>

<p align="center">
  <a href="https://macrokit.dev">macrokit.dev</a>
</p>

---

## What it is

Macrokit is a runtime + SDK for shipping LLM applications under cloud-API constraints — data residency, compliance, air-gapped networks, or budget. It works by moving multi-step reasoning to **design-time** (a strong model encodes a workflow once as a deterministic macro) so the weak model only does **intent classification** at runtime ("user wants X → call macro Y").

The hard part for weak models is multi-step reasoning. The easy part is routing. Macrokit pushes the hard part offline so cheap/local models can do the routing reliably.

## Where it's headed

Launching publicly in Q3 2026 — see [macrokit.dev](https://macrokit.dev) for the launch essay and quickstart.

## Built by

Built by the team behind [Deakee](https://deakee.com) and a private production system that has been running this architecture in cross-border commerce since early 2026.

## License

Apache 2.0. See the LICENSE file in each repository.
