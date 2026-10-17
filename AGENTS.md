# AGENTS.md

This repository is a Samman Learning Hour on DORA software delivery performance metrics, published as a Just the Docs
site from `docs/`. It holds documentation only; there is no application code.

## Language

Use the terms in `GLOSSARY.md` verbatim in every page and commit. Read it before writing or editing content, and add a
term there when a new one is settled.

## Site structure

Pages follow the Diátaxis split, one Just the Docs parent page per section:

- `docs/index.md`: the Learning Hour itself (learning goals plus the Connect, Concept, Concrete Practice, Conclusions
  phases with timings). Keep its timings and prompts in sync with the Facilitation Guide.
- `docs/how-to/`: the Facilitation Guide, written as numbered steps for the Facilitator.
- `docs/explanation/`: background reading for Participants.

## Page conventions

- Front matter carries `title`, `layout`, `parent` and `nav_order`.
- Each page opens with an H1 marked `{: .no_toc }`, a lead paragraph marked `{: .fs-6 .fw-300 }`, then a TOC block.
- Phase headings read `## <Phase>: <activity> (⏱️ N min)`.
- Links are reference-style, collected at the bottom of the page. Internal links use `{% link path.md %}`.
- Metric definitions come from https://dora.dev/guides/dora-metrics/; credit DORA wherever they are quoted.

## Workflow

- Preview locally with `./docs/start_local_server.sh`.
- Commit messages use conventional commits (`docs:`, `feat:`, `chore:`).
