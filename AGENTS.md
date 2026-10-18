# AGENTS.md

This repository is a Samman Learning Hour on DORA software delivery performance metrics, published as a Just the Docs
site from `site/`. It holds documentation only; there is no application code.

## Language

Use the terms in `GLOSSARY.md` verbatim in every page and commit. Read it before writing or editing content, and add a
term there when a new one is settled.

## Site structure

Pages follow the Diátaxis split, one Just the Docs parent page per section:

- `site/index.md`: the Learning Hour itself (learning goals plus the Connect, Concept, Concrete Practice, Conclusions
  phases with timings). Keep its timings and prompts in sync with the Facilitation Guide.
- `site/how-to/`: the Facilitation Guide, written as numbered steps for the Facilitator.
- `site/reference/`: facts to look up during the Learning Hour, such as the five DORA metrics.
- `site/explanation/`: background reading for Participants.

`docs/research/` sits outside the site and is not published. It holds research notes that back the pages. Research
runs draw on the source list in `.nwave/trusted-source-domains.yaml`.

## Page conventions

- Front matter carries `title`, `layout`, `parent` and `nav_order`.
- Each page opens with an H1 marked `{: .no_toc }`, a lead paragraph marked `{: .fs-6 .fw-300 }`, then a TOC block.
- Phase headings read `## <Phase>: <activity> (⏱️ N min)`.
- Links are reference-style, collected at the bottom of the page. Internal links use `{% link path.md %}`.
- Metric definitions come from https://dora.dev/guides/dora-metrics/; credit DORA wherever they are quoted.

## Workflow

- Preview locally with `./site/start_local_server.sh`.
- Commit messages use conventional commits (`docs:`, `feat:`, `chore:`).
