---
title: gasx CLI
category: Ecosystem
order: 1
---

For compiling `.gas` to `.go`, create new projects, 
generate css rules by atomic css class names 
and for many other development things you can use official cli: [gasx](https://github.com/gascore/gasx)

## `.gas` syntax

In order to make your development easily you can use gasx translator.
gasx can translate your html-like code to valid golang code for using it in components.

Gas templates syntax similar to vue templates syntax. It using xml tags for contains different type of code in one file.
Valid gas template file need contain these tags:

1. `<script>` - golang code
2. `<template>` - html-like code. It translates in golang.

And optional `<style>` tag it require supportStyle flag. For more information see [gas and styles](https://gascore.github.io/styles)

Example:
```
<template>
    <main>
        ...
    </main>
</template>
<script>
...
func getComponent(...) *gas.Component {
    return gas.NewComponent(
        &gas.Component{
            ...
        },
        fileT,)
}
...
var fileT gas.GetComponentChildes
</script>

<style>
    main {
        a {
            color: #00cc99;
        }
    }
</style>
```
(where file name is `file`).

**REMEMBER**:

You can't use `<fileName>T` string in gas templates.
Because in compiling gasx replace first `<fileName>T` string in `<script>` by generated from `<template>` code.
> You can add `var <fileName>T gas.GetComponentChildes` after component for make your code valid for syntax highlighters.

#### External components
For add external components in template use `<e>` tag with `run` attribute.
Example: `<e run="externalFunction(some, function, values)" />`.


## "new" command

`gasx new` generate new gas project. 
You can select futures needful for you by selecting one three templates:

1. `default` -- standard gas application using gas and gas-web
2. `router` -- `default`  with included gas-router
3. `full` -- `router` with included gas-store

If you create project not in your GOPATH/src you need to fix your imports.

## "compile" command

`gasx compile` translate `.gas` files to valid golang code.

If you want to add "_gas" prefix to generated files use "-w" (writeSuffix) flag.

For generate css from your `<style>` tags use "-s" (styles) flag. (you can change output css file name by "-o" flag)

## "css" commands

`gasx css minify` just minify css files

`gasx css acss` create css styles by classes in `.gas` files. 
It's analogue for [atomizer](https://github.com/acss-io/atomizer) written in pure go.
gasx atomizer have same rules with [acss.io](https://acss.io/atomic-classes.html), but there can be little differences.
To find out what acss is see [official atomic css site](https://acss.io).
If you want more see: [atomic css documentation](https://acss.io/quick-start.html) and [gas and styles page](https://gascore.github.io/styles)