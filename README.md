# yggdrasil-repo-template

I wanted every new repo of mine to run the same CI from its very first PR, without copying workflows around by hand. So this is the template that [yggdrasil](https://github.com/zimmertr/yggdrasil)'s Terraform creates each new repo from.

## What's in It

- **PR Title** - `.github/workflows/pr-title.yml` calls yggdrasil's `pr-title` module, which refuses any PR title that isn't `type(scope): summary`.
- **Lint** - `.github/workflows/lint.yml` calls yggdrasil's `lint` module: actionlint, zizmor and Semgrep over the workflows, shellcheck over the scripts, and a check of the docs' links and em dashes.
- **Renovate** - `.github/renovate.json` extends yggdrasil's shared preset, so Renovate keeps the module pins and everything else current.

## Using It

You don't use this template by hand. Instead, a PR to yggdrasil adds `repos/<owner>/<name>.yml`, and its merge creates the repo from here with every setting and ruleset. Afterwards, run `/initialize-project` in the new repo. It replaces this README with the project's own, and adds the `LICENSE`, `.gitignore` and anything else the project needs, such as Scorecard on a public repo.
