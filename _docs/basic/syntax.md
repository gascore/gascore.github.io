---
title: Syntax
category: Basic
order: 3
---

Gas uses html-like syntax in `<template>`, it allows you create logic stuff like: if, for and others.
Here the specific template rules:

## Dynamic text

You can add *dynamic text* by `{% raw %}{{{% endraw %}` and `{% raw %}}}{% endraw %}`
Syntax: `{% raw %}{{ <your code> }}{% endraw %}` - your code should return string (maybe add support for other types in the future)

```{% raw %}
<h1 id="title-h1" class="title is-1">
    {{ this.GetData("text").(string) }}
</h1>
{% endraw %}```

## Handlers - handler allow you catch element event and some stuff.

Syntax: `g-on:<event-name>="<your code>"` (`<your code>` should return error).

```
<button g-on:click="this.SetData(`click`, this.GetData(`click`).(int)+1))">
    Click
</button>
```

## Binds - updating value for element attributes.

Syntax: `g-bind:<attribute name>="<your code>"` (`<your code>` should return string).

```
<h1 g-bind:color="this.GetData(`color`).(string)">
    Colored text
</h1>
```

## For directive - render a list of items based on an array.

Syntax: `g-for="<index name(can be ignored)>, <element name> in <data name>"`
Data name it's key for array in `this.GetData`,
but if you add `@` before data name for directive will data name like *raw* data.

```{% raw %}
<li g-for="i, el in arrayName">
    {{ fmt.Sprintf("%d", i) }}: {{ el.(string) }}
</li>
{% endraw %}```

or with *raw* data

```{% raw %}
...
array := []string{"lorem", "ipsum"}
...
<li g-for="i, el in @array">
    {{ fmt.Sprintf("%d", i) }}: {{ el.(string) }}
</li>
{% endraw %}```
(but array will don't update after array changed)

## If directive - conditional block for your component rendering.

Syntax: `g-if="<your code>"` - your code should return bool.

```
<h1 g-if="this.GetData(`accountBalance`).(int) > 1000">
    I'm so rich!
</h1>
```

#### Show directive - like If directive but hiding your component by css styles (it will render from first parent render tick)


## Model directive - dynamic updating your data after element value has changed.

Your data type should be compared with input (textarea, select) type:

| Element                       | Variable type |
|-------------------------------|---------------|
| input (type range or number)  | int           |
| select, input (type checkbox) | bool          |
| textarea, input(other types)  | string        |

Syntax: `g-model="<key for data value>"`

```
<input g-model="currentText" />
```

## html directive - replace element innerHtml to this computed value

Syntax: `g-html="<your code>"` - your code should return string

```
<p g-html="this.GetData(`markdownhtmled`).(string)"></p>
```
