---
title: "X Could not find Module `Prelude` fix"
date: 2022-07-12T02:27:11+01:00
draft: false
tags: ["Haskell","Fix", "Programming"]
author: "Diogo Valério"
---

Today I was experimenting with Haskell and this error struck me:

> X Could not find Module `Prelude`</p>
> There are files missing in the `base-x-x-x` package,</p>

This has an easy fix:

Install the `ghc-static` package

```bash
sudo pacman -S ghc-static 
```

Then all should compile easily.
