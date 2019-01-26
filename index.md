---
title: Gas framework introduction
---

This is gas framework documentation. Here you can learn new about [gas-core](https://github.com/gascore/gas), [gas-web](https://github.com/gascore/gas-web), [gasx](https://github.com/gascore/gasx), [gas-router](https://github.com/gascore/gas-router).

### What is gas?

Gas -- golang framework for building frontend (only yet) GUI applications

### How it works?

Gas is module system.
Main part is [gas-core](https://github.com/gascore/gas) - it contains all logic (for render, updates, e.t.c.)

gas-core uses *backends* which render your components to user ui. *Backend* can be not only for web, but for anything where you can run golang(mobile, terminal, desktop).
But now exist only one backend - [gas-web](https://github.com/gascore/gas-web) which use WASM or [gopherjs](https://github.com/gopherjs/gopherjs) for render.

With gas-web you can use [gas-router](https://github.com/gascore/gas-router) - simple web router

## Examples?

Of course, there many examples:

1. [Main example](https://gascore.github.io/examples/router) - biggest example, shows all gas-ecosystem technologies for this moment. Code [here](https://github.com/gascore/example)
2. [TODO-MVC example](https://gascore.github.io/examples/todo)
3. [Basic examples](https://github.com/gascore/gas/blob/master/examples) (hosting in [jsgo.io](https://jsgo.io))

> Feel free to send us a message at [nowasmawesome@gmail.com](mailto:nowasmawesome@gmail.com) with your feedback.

