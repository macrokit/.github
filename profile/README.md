<p align="center">
  <img src="./wordmark.svg" alt="Macrokit" width="320">
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

It recapitulates how brains manage the cost of thinking: a slow, expensive *deliberation* path (System 2 — the strong model) compiles repeated reasoning into a fast, cheap *automatic* path (System 1 — the macro), and the distillation gate compiles deliberation into reflex through repetition. A fast cheap reflex and a slow expensive mind, with the reflex carrying the load.

It's also an **open format for macros** — the deterministic, distilled form of a workflow. A *skill* tells a strong model how to think; a *macro* is the compiled result that runs on weak/local models. Macros can call MCP tools as primitives — Macrokit sits above MCP, not against it.

## Where it's headed

Launching publicly in Q3 2026 — see [macrokit.dev](https://macrokit.dev) for the launch essay and quickstart.

## Build on top

Macrokit deliberately keeps curated examples small. Vertical macro libraries live as standalone npm packages you publish yourself — see [`CONTRIBUTING_MACROS.md`](https://github.com/macrokit/core/blob/main/CONTRIBUTING_MACROS.md) and the [community registry](./community) for the listing process.

The registry is the seed of a broader ecosystem: a place to share and discover the vertical macro libraries authors build, so adopting a new vertical can start from proven macros instead of a cold start.

## Built by

Built on a private production system that has been running this architecture in operations tooling for users without frontier-API access since early 2026.

## License

Apache 2.0. See the LICENSE file in each repository.
