---
title: External components
category: Basic
order: 4
---

For add external components in template use `<e>` tag with `run` attribute.
Example: `<e run="externalFunction(some, function, values)" />`.

`<e>` childes translates to [External](https://github.com/gascore/gas/blob/master/external.go) 
structure and appends to the end of `run` attribute:
1. Childes with `name` attribute appends to `Slots`: `<h1 name="bar">Foo</h1>` => `"bar": gas.NE(...)`.
2. `template` childes appends to `Templates`. `<template name="bar">Foo</template>` => `"bar": func(values ...interface{})*gas.C{...}`
3. Other childes appends to `Body`.

## Templates

Templates is a functions taking values (`...interface{}`) and returning component (`*gas.C`).
Templates have `types` attribute using for create values aliases: `types="a := values[0].(int); b := values[1].(int)"`.