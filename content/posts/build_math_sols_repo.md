---
title: "建立數學解答庫"
date: 2023-08-16T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "Math"
---

一直想把 20 年前在 BBS 上寫的 [數學解答](https://solutions.hjwu.me/) 貼出來，但不論是 [Jekyll](https://jekyllrb.com/) 或是 [HUGO](https://gohugo.io/) 都對 $\LaTeX$ 不那麼友善。直到最近看到 [Docusaurus](https://docusaurus.io/) 才覺得驚為天人。

## 操作備忘

基本上 [官方文件](https://docusaurus.io/docs) 算蠻清楚了。

+ 建議使用 [yarn](https://yarnpkg.com/) 執行一切指令。因為不管 [發佈到 Github](https://docusaurus.io/docs/deployment#triggering-deployment-with-github-actions) 或是 [發佈到 GitLab](https://tw-docs.com/docs/static-site-generators/docusaurus-gitlab-pages/#create-ci-configuration) 的設定都以 `yarn`為主。

{{< tabgroup align="right" style="code" >}}
    {{< tab name="GitHub" >}}
```yml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
    # Review gh actions docs if you want to further define triggers, paths, etc
    # https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#on

jobs:
  deploy:
    name: Deploy to GitHub Pages
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
          cache: yarn

      - name: Install dependencies
        run: yarn install --frozen-lockfile
      - name: Build website
        run: yarn build

      # Popular action to deploy to GitHub Pages:
      # Docs: https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-docusaurus
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          # Build output to publish to the `gh-pages` branch:
          publish_dir: ./build
          # The following lines assign commit authorship to the official
          # GH-Actions bot for deploys to `gh-pages` branch:
          # https://github.com/actions/checkout/issues/13#issuecomment-724415212
          # The GH actions bot is used by default if you didn't specify the two fields.
          # You can swap them out with your own user credentials.
          user_name: github-actions[bot]
          user_email: 41898282+github-actions[bot]@users.noreply.github.com
```
    {{< /tab >}}
    {{< tab name="GitLab" >}}
```yml
image: node:latest

# allow caching for faster deployment
cache:
  paths:
    - node_modules/
    - public/
    - .cache/

pages:
  stage: deploy
  script:
    - yarn install
    - yarn build:gitlab
  artifacts:
      paths:
        - public
  only:
    - main
```
    {{< /tab >}}  
{{< /tabgroup >}}

+ 如果要在 [GitHub](https://github.com/) 上放 `CNAME` 的話，要把它放在 **static** 資料夾裡面，不然每次重 build 都會被移除，感覺 [GitLab](https://gitlab.com/) 的設計比較簡單。

## 是否搬家 ?

其實有糾結是否要放棄 [HUGO](https://gohugo.io/) 改用 [Docusaurus](https://docusaurus.io/)，但發現它的 node_modules 這包資料夾超巨大而且 Build 速度很慢。而且也剛好看到這篇 [Moving from Docusaurus to Hugo](https://ricard.dev/moving-from-docusaurus-to-hugo/) 有寫類似的內容。所以還是繼續留在 [HUGO](https://gohugo.io/) 吧。 ☕