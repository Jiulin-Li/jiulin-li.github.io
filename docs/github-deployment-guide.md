# GitHub Pages Deployment Guide

## Current Repository

This repository currently points to:

- `MonsterPPPP/jiulin-li.github.io`

Because the repository owner is `MonsterPPPP` and the repository name is not
`MonsterPPPP.github.io`, GitHub Pages treats this as a project site. The
expected public URL is:

```text
https://monsterpppp.github.io/jiulin-li.github.io/
```

The matching Jekyll settings are:

```yml
url: https://monsterpppp.github.io
baseurl: "/jiulin-li.github.io"
repository: "MonsterPPPP/jiulin-li.github.io"
```

## Root `index.html`

Do not add a hand-written root-level `index.html` for this site.

The homepage is `_pages/about.md`, which has:

```yml
permalink: /
```

During the Jekyll build, that page is generated as `_site/index.html`. Adding a
second root homepage file can create duplicate output paths.

## Deployment Mode

Use GitHub Pages' built-in branch deployment for this repository:

1. Open `Settings`.
2. Open `Pages`.
3. Under `Build and deployment`, set `Source` to `Deploy from a branch`.
4. Set `Branch` to `master`.
5. Set the folder to `/(root)`.
6. Save.

GitHub will then run its own `pages build and deployment` workflow when `master`
is pushed. That built-in workflow is the one that publishes the site.

This repository also includes `.github/workflows/pages.yml`, but that workflow
is only a build check. It runs Jekyll and verifies that the site can be generated
without calling the GitHub Pages API. It intentionally does not use
`actions/configure-pages` or `actions/deploy-pages`, because those actions fail
with `Get Pages site failed` when the repository is not configured for
GitHub Actions based Pages deployment.

After the built-in Pages deployment finishes, the site should be available at:

```text
https://monsterpppp.github.io/jiulin-li.github.io/
```

## Push Commands

From the repository root:

```bash
git add -A
git commit -m "Configure GitHub Pages branch deployment"
git push origin master
```

## If You Want `https://monsterpppp.github.io/`

Rename or recreate the GitHub repository as:

```text
MonsterPPPP.github.io
```

Then change `_config.yml` to:

```yml
url: https://monsterpppp.github.io
baseurl: ""
repository: "MonsterPPPP/MonsterPPPP.github.io"
```

The build-check workflow can stay as-is, but the GitHub Pages branch source must
then point to the renamed repository's default branch.

## If You Want `https://jiulin-li.github.io/`

That requires either:

- a GitHub account or organization named `jiulin-li` with a repository named
  `jiulin-li.github.io`, or
- a custom domain configured through GitHub Pages and DNS.

The repository name alone is not enough to claim `https://jiulin-li.github.io/`
when the repository owner is `MonsterPPPP`.
