---
title: Overview
---

### What is gas?

Gas -- golang framework for building frontend (only yet) GUI applications

### How it works?

Gas is module system.
Main part is [gas-core](https://github.com/gascore/gas) - it contains all logic (for render, updates, e.t.c.)

gas-core uses *backends* which render your components to user ui. *Backend* can be not only for web, but for anything where you can run golang(mobile, terminal, desktop).
But now exist only one backend - [gas-web](https://github.com/gascore/gas-web) which use WASM or [gopherjs](https://github.com/gopherjs/gopherjs) for render.

With gas-web you can use [gas-router](https://github.com/gascore/gas-router) - simple web router