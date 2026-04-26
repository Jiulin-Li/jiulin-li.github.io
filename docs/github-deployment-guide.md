# GitHub Deployment Guide

## Purpose

本文档说明如何把这个仓库发布为 GitHub Pages 站点，以及当前仓库名对最终访问地址的影响。

## Current Repository Situation

当前远端仓库是：

- `MonsterPPPP/jiulin-li.github.io`

这不是 GitHub 用户根站仓库，因此默认 Pages 地址不是根域名，而是：

- `https://monsterpppp.github.io/jiulin-li.github.io/`

如果你希望直接通过 `https://monsterpppp.github.io/` 打开，仓库名必须改成：

- `MonsterPPPP.github.io`

并且站点配置中的 `baseurl` 需要改成空字符串。

## Step 1: Push Local Changes

在项目根目录执行：

```bash
git add -A
git commit -m "your commit message"
git push origin master
```

如果你使用的是 HTTPS 远端，也可以是：

```bash
git remote set-url origin https://github.com/MonsterPPPP/jiulin-li.github.io.git
git push origin master
```

## Step 2: Enable GitHub Pages

在 GitHub 网页端进入该仓库：

1. 打开仓库主页
2. 点击 `Settings`
3. 点击左侧 `Pages`
4. 在 `Build and deployment` 中选择 `Deploy from a branch`
5. `Branch` 选择 `master`
6. 目录选择 `/(root)`
7. 点击 `Save`

等待 GitHub 构建完成后即可访问页面。

## Step 3: Access URL

如果仓库保持为 `MonsterPPPP/jiulin-li.github.io`，则访问：

```text
https://monsterpppp.github.io/jiulin-li.github.io/
```

## Step 4: If You Want Root-Domain Access

如果你想直接通过：

```text
https://monsterpppp.github.io/
```

访问主页，需要这样做：

1. 在 GitHub 上新建或重命名仓库为 `MonsterPPPP.github.io`
2. 把本地仓库远端指向新仓库
3. 把 `_config.yml` 改成：

```yml
url: https://monsterpppp.github.io
baseurl: ""
```

4. 再次提交并推送
5. 在 GitHub Pages 中继续选择 `master / (root)` 发布

## Step 5: If You Want a Custom Domain

如果你有自己的域名，例如：

- `yourdomain.com`

可以在 GitHub `Settings -> Pages` 中填写 `Custom domain`，然后去 DNS 服务商处配置：

- 子域名通常使用 `CNAME`
- 根域名通常使用 `A`、`ALIAS` 或 `ANAME`

同时把 `_config.yml` 改成：

```yml
url: https://yourdomain.com
baseurl: ""
```

如果使用自定义域名，通常还会在仓库根目录放一个 `CNAME` 文件，文件内容就是该域名本身。

## Notes

- 如果页面样式异常，先检查 `_config.yml` 中的 `url` 和 `baseurl` 是否与仓库实际结构匹配。
- 如果仓库名不是 `用户名.github.io`，那最终站点就一定会带仓库路径。
- GitHub Pages 初次启用后可能需要几分钟到十几分钟才会生效。
