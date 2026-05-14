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

## Deployment Workflow

This repository includes `.github/workflows/pages.yml`. It builds the Jekyll
site and deploys the generated `_site` artifact whenever `master` is pushed.

This workflow requires the repository Pages source to be `GitHub Actions`. If
`actions/configure-pages` fails with `Get Pages site failed` or `Not Found`,
the repository has not been enabled for GitHub Actions based Pages deployment
yet.

On GitHub, configure the repository as follows:

1. Open `Settings`.
2. Open `Pages`.
3. Under `Build and deployment`, set `Source` to `GitHub Actions`.
4. Push to `master`, or run the `Deploy Jekyll site to Pages` workflow manually.

After the workflow finishes, the site should be available at:

```text
https://monsterpppp.github.io/jiulin-li.github.io/
```

Do not choose `Deploy from a branch` while keeping this workflow enabled. That
is a different Pages deployment mode; using both makes the Actions workflow fail
or become redundant.

## Push Commands

From the repository root:

```bash
git add -A
git commit -m "Configure GitHub Pages deployment"
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

The same GitHub Actions workflow can still deploy the site.

## If You Want `https://jiulin-li.github.io/`

That requires either:

- a GitHub account or organization named `jiulin-li` with a repository named
  `jiulin-li.github.io`, or
- a custom domain configured through GitHub Pages and DNS.

The repository name alone is not enough to claim `https://jiulin-li.github.io/`
when the repository owner is `MonsterPPPP`.
