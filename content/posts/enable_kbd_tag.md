---
title: "啟用 kbd tag"
date: 2023-01-04T00:25:00+08:00
draft: false
dropCap: false
tags:
  - "Hugo"
---

一直好奇為什麼 `kbd` tag 在某些 theme 一直無法正確呈現，剛剛才發現原始碼有這段 `<!-- raw HTML omitted -->`。

Google 後發現 [Raw HTML getting omitted in 0.60.0](https://discourse.gohugo.io/t/raw-html-getting-omitted-in-0-60-0/22032) 所以表示這是老問題了。解法可以在 *config.toml* 加入這段

```toml
[markup.goldmark.renderer]
unsafe= true
```

但看到 `unsafe= true` 總覺得彆扭，所以我決定採取使用 `shortcodes` 來處理。

1. 參考這篇 [讓你的 Markdown 有更漂亮的鍵盤按鍵表示方式](https://ouch1978.github.io/docs/docusaurus/customization/apply-kbd-style-in-markdown) 新增 *assests\kbd.css*。
2. 調整 *config.toml* 為 `customCSS = ["kbd.css"]`
3. 新增 *layouts\shortcodes\kbd.html*