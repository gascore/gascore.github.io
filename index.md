---
title: Gas framework introduction
---

# What is gas?

Gas is golang framework for building ui. 
Gas isn't a monolithic framework, gas have *core* and *backend*'s. 
[Core](https://github.com/gascore/gas) contains all logic stuff (render, updates, e.t.c.). 
*Backend* render your application to specific platform. platform can be anything where you can run golang (web, mobile, terminal, desktop),
but now exist only one backend -- [gas-web](https://github.com/gascore/gas-web) which use web assembly or [gopherjs](https://github.com/gopherjs/gopherjs) for render.

# [Get started](https://gascore.github.io/basic/overview)

# Examples

There are many examples:

1. [Main example](https://gascore.github.io/examples/router) - biggest example, shows all gas-ecosystem technologies for this moment. Code [here](https://github.com/gascore/example)
2. [TODO-MVC example](https://gascore.github.io/examples/todo)
3. [Basic functional examples](https://github.com/gascore/gas/blob/master/examples) (hosting in [jsgo.io](https://jsgo.io))

> Feel free to send us a message at [our mail](mailto:nowasmawesome@gmail.com) with your feedback.

