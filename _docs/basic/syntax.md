---
title: Syntax
category: Basic
order: 3
---

In `<template>` gas uses html-like markup syntax. Here the template rules:

## Dynamic text

You can add *dynamic variables* by `{% raw %}{{{% endraw %}` and `{% raw %}}}{% endraw %}`
Syntax: `{% raw %}{{ <your code> }}{% endraw %}` - your code should return string or number.

```{% raw %}
<h1 id="title-h1" class="title is-1 c(#00cc99)">
    {{ this.GetData("text") }}
</h1>
{% endraw %}```

## Handlers
Event handlers for elements.
Syntax: `g-on:<event-name>="<your code>"` (`<your code>` should return error).

```
<button g-on:click="this.SetData(`click`, this.GetData(`click`).(int)+1))">
    Click
</button>
```

## Binds
Element attribute with binded value.
Syntax: `g-bind:<attribute name>="<your code>"` (`<your code>` should return string).

```
<h1 g-bind:color="this.GetData(`color`)">
    Colored text
</h1>
```

## If-directive
Conditional block for components rendering.
Syntax: `g-if="<your code>"` - your code should return bool.

```
<h1 g-if="this.GetData(`accountBalance`).(int) > 1000">
    I'm so rich!
</h1>
```

## Show-directive
Same with if-directive but show-directive render component and hide it by css styles.

## For-directive
Render a list of elements by array.

Syntax: `g-for="<index name(can be ignored)>, <element name> in <data name>"`.
Data name is a key for array in `this.GetData`, 
but if you add `@` before data name for-directive will use it as variable.

For-directive uses only array of interfaces(`[]interface{}`)

```{% raw %}
...
Data: map[string]interface{} {
    "arrayName": []interface{}{"foo","bar"},
},
...
<li g-for="i, el in arrayName">
    {{ fmt.Sprintf("%d", i) }}: {{ el }}
</li>
{% endraw %}```

or with *raw* data

```{% raw %}
...
array := []string{"foo", "bar"}
...
<li g-for="i, el in @array">
    {{ fmt.Sprintf("%d", i) }}: {{ el }}
</li>
{% endraw %}```
(but with raw array elements won't update after changes)

## Model-directive
Binding data to element input, textarea, select, etc.
Syntax: `g-model="<key for data value>"`. You can *deep data keys* for bind structure attribute, array or map element.

```
<input g-model="currentText" />
```

or with *deep keys*

```
<input g-model="user.Email" />
<textarea g-model="user.Stories[0].Text"></textarea>
```

Data type will be compared with input type:

| Element                       | Variable type |
|-------------------------------|---------------|
| input (type range or number)  | int           |
| select, input (type checkbox) | bool          |
| textarea, input(other types)  | string        |

## html-directive
Replace element innerHtml with computed value.
Syntax: `g-html="<your code>"` - your code should return string

```
<p g-html="this.GetData(`markdownhtmled`)"></p>
```
