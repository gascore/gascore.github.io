---
title: Gas templates
category: Basic
order: 2
---

In order to make your development easily you can use gasx translator.
gasx can translate your html-like code to valid golang code for using it in components.

Gas templates syntax similar to vue templates syntax. It using xml tags for contains different type of code in one file.
Valid gas template file need contain these tags:

1. `<script>` - go code
2. `<template>` - html-like code translated into go code
3. `<style>` - css (scss, sass, etc) styles

Example `.gas` file:
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
(here file name is `file`).

### Where does the parsed `<template>` go?

Compiled from `<template>` code pasting instead first `<fileName>T` string.
It's seems like:
```
return gas.NewComponent(
    &gas.Component{},
    <fileName>T,)
```

It's bad way, but I don't know better, 
and don't forget if you want to paste `<fileName>T` you can create variable after your component declaration.

> You can add `var <fileName>T gas.GetComponentChildes` after component for make your code valid for any syntax highlighter.