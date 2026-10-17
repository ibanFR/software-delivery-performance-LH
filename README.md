# Software Delivery Performance Learning Hour

A [Samman Learning Hour] that introduces the five [DORA] software delivery performance metrics to a cross-team
community of practice. The Learning Hour is published as a [Just the Docs] site from the `docs` folder.

## What's inside

- `docs/index.md`: the Learning Hour description, with learning goals and the four phases
- `docs/how-to/facilitation-guide.md`: how to prepare and run the session
- `docs/explanation/dora-metrics.md`: background reading on the metrics and their pitfalls
- `GLOSSARY.md`: the language used across this repository
- `.github/workflows/pages.yml`: builds and deploys the site to GitHub Pages when `docs/**` changes on `main`

## Building and previewing the site locally

Assuming [Jekyll] and [Bundler] are installed, run `./docs/start_local_server.sh` from anywhere in the repository. It
installs any missing gem dependencies and serves the site with live reload at `localhost:4000`.

## Licensing and Attribution

This repository was created from the [learning-hour-template] and uses the [Just the Docs] theme, whose MIT License is
included in the `docs/` folder.

The metric definitions and pitfalls are based on the [DORA metrics guide].

All documentation content within the `docs/` folder is authored by Iván Fernández and licensed under the
[Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0) License].

[Samman Learning Hour]: https://sammancoaching.org/reference/learning_hour_definition.html
[DORA]: https://dora.dev/
[DORA metrics guide]: https://dora.dev/guides/dora-metrics/
[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[Jekyll]: https://jekyllrb.com
[Bundler]: https://bundler.io
[learning-hour-template]: https://github.com/ibanFR/learning-hour-template
[Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0) License]: https://creativecommons.org/licenses/by-sa/4.0/
