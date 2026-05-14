# GitHub Pages Deployment Guide

## Current Deployment Model

This project currently uses two GitHub repositories:

- Source/upstream repository: `MonsterPPPP/jiulin-li.github.io`
- Live Pages repository: `Jiulin-Li/jiulin-li.github.io`

The live repository is a fork of the source repository. GitHub Pages is enabled
on the fork, not on the upstream repository. The public site URL is therefore:

```text
https://jiulin-li.github.io/
```

The matching Jekyll settings are:

```yml
url: https://jiulin-li.github.io
baseurl: ""
repository: "Jiulin-Li/jiulin-li.github.io"
```

Do not use the `MonsterPPPP` URL in `_config.yml` when deploying from
`Jiulin-Li/jiulin-li.github.io`; otherwise the generated HTML will point CSS,
JavaScript, canonical URLs, feeds, and navigation links at the wrong site.

## Important Fork Behavior

Pushing to `MonsterPPPP/jiulin-li.github.io` does not automatically publish the
`Jiulin-Li/jiulin-li.github.io` site.

For GitHub Pages branch deployment, the commit must reach the publishing source
repository and branch. In this setup, that means:

```text
Jiulin-Li/jiulin-li.github.io
master
/(root)
```

If you edit and push only to the upstream repository, the fork's site will not
change until the fork is synced or the same commit is pushed to the fork.

## Root `index.html`

Do not add a hand-written root-level `index.html` for this site.

The homepage is `_pages/about.md`, which has:

```yml
permalink: /
```

During the Jekyll build, that page is generated as `_site/index.html`. Adding a
second root homepage file can create duplicate output paths.

## GitHub Pages Settings

In the live repository `Jiulin-Li/jiulin-li.github.io`, configure Pages like
this:

1. Open `Settings`.
2. Open `Pages`.
3. Under `Build and deployment`, set `Source` to `Deploy from a branch`.
4. Set `Branch` to `master`.
5. Set the folder to `/(root)`.
6. Save.

GitHub should then run a `pages build and deployment` workflow whenever someone
with admin permission and a verified email address pushes to the publishing
source branch.

## Local Remotes

The local repository may keep `MonsterPPPP/jiulin-li.github.io` as `origin`, but
you also need a remote for the live Pages fork:

```bash
git remote add pages git@github.com:Jiulin-Li/jiulin-li.github.io.git
```

To update both repositories:

```bash
git push origin master
git push pages master
```

If `git push pages master` does not run, the live site will not receive your
latest commit.

## Debug Checklist

Use these checks when a commit does not appear on the site:

1. Confirm the live site URL:

   ```bash
   curl -I https://jiulin-li.github.io/
   ```

2. Confirm the live fork has the latest commit:

   ```bash
   git ls-remote git@github.com:Jiulin-Li/jiulin-li.github.io.git HEAD refs/heads/master
   git rev-parse HEAD
   ```

   The commit hashes should match.

3. Check the live fork's Actions tab:

   ```text
   https://github.com/Jiulin-Li/jiulin-li.github.io/actions
   ```

   For branch deployment, look for `pages build and deployment`, not only the
   custom `Build Jekyll site` check.

4. Check whether the generated HTML is using the correct base URL:

   ```bash
   curl -L https://jiulin-li.github.io/ | grep -i "monsterpppp.github.io"
   ```

   This should return nothing. If it returns links, `_config.yml` still points
   at the wrong deployment target.

5. If `pages build and deployment` does not appear after a push, re-check the
   Pages settings in `Jiulin-Li/jiulin-li.github.io`, not in the upstream
   `MonsterPPPP` repository.

## If You Deploy From `MonsterPPPP/jiulin-li.github.io` Instead

If you decide to publish the upstream repository directly, it is a project site,
not a user root site. Its URL would be:

```text
https://monsterpppp.github.io/jiulin-li.github.io/
```

For that deployment target only, `_config.yml` should instead be:

```yml
url: https://monsterpppp.github.io
baseurl: "/jiulin-li.github.io"
repository: "MonsterPPPP/jiulin-li.github.io"
```
