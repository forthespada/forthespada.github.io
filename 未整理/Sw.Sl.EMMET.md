---
title: EMMET
date: 2018-06-26
description: Emmet uses syntax similar to CSS selectors for describing elements’ positions inside generated tree and elements’ attributes.
---
## [Abbreviations Syntax](https://docs.emmet.io/)

Emmet uses syntax similar to CSS selectors for describing elements’ positions inside generated tree and elements’ attributes.

## Elements

<div class="note info">输入div后，回车或者按下<kbd>tab</kbd>键，即可生成`<div></div>`。</div>

You can use elements’ names like `div` or `p` to *generate* HTML tags. Emmet doesn’t have a predefined set of available tag names, you can write any word and transform it into a tag: `div` → `<div></div>`, `foo` → `<foo></foo>` and so on.

## Nesting operators

Nesting operators are used to position abbreviation elements inside generated tree: whether it should be placed inside or near the context element.

### Child: `>`

<div class="note info">子元素使用 `>` </div>

You can use `>` operator to nest elements inside each other:

```html
div>ul>li
```

...will produce

```html
<div>
    <ul>
        <li></li>
    </ul>
</div>
```

### Sibling: `+`

<div class="note info">兄弟元素使用 `+` </div>

Use `+` operator to place elements near each other, on the same level:

```html
div+p+bq
```

...will output

```html
<div></div>
<p></p>
<blockquote></blockquote>
```

### Climb-up: `^`

<div class="note info">将元素的级提升 `^` </div>

With `>` operator you’re descending down the generated tree and positions of all sibling elements will be resolved against the most deepest element:

```html
div+div>p>span+em 
```

...will be expanded to

```html
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
```

With `^` operator, you can climb one level up the tree and change context where following elements should appear:

```html
div+div>p>span+em^bq
```

...outputs to

```html
<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>
```

You can use as many `^` operators as you like, each operator will move one level up:

```HTML
div+div>p>span+em^^^bq
```

...will output to

```html
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
<blockquote></blockquote>
```

### Multiplication: `*`

<div class="note info">生成多个相同元素 `*` </div>

With `*` operator you can define how many times element should be outputted:

```html
ul>li*5
```

...outputs to

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

### Grouping: `()`

<div class="note info">分组元素 `()` </div>

Parenthesises are used by Emmets’ power users for grouping subtrees in complex abbreviations:

```html
div>(header>ul>li*2>a)+footer>p
```

...expands to

```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

If you’re working with browser’s DOM, you may think of groups as Document Fragments: each group contains abbreviation subtree and all the following elements are inserted at the same level as the first element of group.

You can nest groups inside each other and combine them with multiplication `*` operator:

```html
(div>dl>(dt+dd)*3)+footer>p
```

...produces

```html
<div>
    <dl>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
    </dl>
</div>
<footer>
    <p></p>
</footer>
```

With groups, you can literally write full page mark-up with a single abbreviation, but please don’t do that.

## Attribute operators

Attribute operators are used to modify attributes of outputted elements. For example, in HTML and XML you can quickly add `class` attribute to generated element.

### ID and CLASS

<div class="note info">对于属性的操作，ID和CLASS可以通过输入`#`,`.`来快速生成。</div>

In CSS, you use `elem#id` and `elem.class` notation to reach the elements with specified `id` or `class` attributes. In Emmet, you can use the very same syntax to *add* these attributes to specified element:

```html
div#header+div.page+div#footer.class1.class2.class3
```

...will output

```html
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>
```

### Custom attributes

<div class="note info">其他的属性则将属性置于`[]`中来生成。</div>

You can use `[attr]` notation (as in CSS) to add custom attributes to your element:

```html
td[title="Hello world!" colspan=3]
```

...outputs

```html
<td title="Hello world!" colspan="3"></td>
```

+ You can place as many attributes as you like inside square brackets.
+ You don’t have to specify attribute values: `td[colspan title]` will produce `<td colspan="" title="">`with tabstops inside each empty attribute (if your editor supports them).
+ You can use single or double quotes for quoting attribute values.
+ You don’t need to quote values if they don’t contain spaces: `td[title=hello colspan=3]` will work.

<div class="note info">如果属性值中不包含空格，则不需要使用引号将属性值包含。</div>

### Item numbering: 

<div class="note info">自动编号 `$`
可在 `$` 后添加 `@n` 修改编号的起始值为n。
    可在 `$` 后添加 `@-` 修改编号的方向。</div>

With multiplication `*` operator you can repeat elements, but with `$` you can *number* them. Place `$` operator inside element’s name, attribute’s name or attribute’s value to output current number of repeated element:

```html
ul>li.item$*5
```

...outputs to

```html
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>
```

You can use multiple `$` in a row to pad number with zeroes:

```html
ul>li.item$$$*5
```

...outputs to

```html
<ul>
    <li class="item001"></li>
    <li class="item002"></li>
    <li class="item003"></li>
    <li class="item004"></li>
    <li class="item005"></li>
</ul>
```

#### Changing numbering base and direction

With `@` modifier, you can change numbering direction (ascending or descending) and base (e.g. start value).

For example, to change direction, add `@-` after `$`:

```html
ul>li.item$@-*5
```

…outputs to

```html
<ul>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
    <li class="item2"></li>
    <li class="item1"></li>
</ul>
```

To change counter base value, add `@N` modifier to `$`:

```html
ul>li.item$@3*5
```

…transforms to

```html
<ul>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
    <li class="item6"></li>
    <li class="item7"></li>
</ul>
```

You can use these modifiers together:

```html
ul>li.item$@-3*5
```

…is transformed to

```html
<ul>
    <li class="item7"></li>
    <li class="item6"></li>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
</ul>
```

## Text: `{}`

<div class="note info">用 `{}` 添加文本内容。</div>

You can use curly braces to add text to element:

```html
a{Click me}
```

...will produce

```HTML
<a href="">Click me</a>
```

Note that `{text}` is used and parsed as a separate element (like, `div`, `p` etc.) but has a special meaning when written right after element. For example, `a{click}` and `a>{click}` will produce the same output, but `a{click}+b{here}` and `a>{click}+b{here}` won’t:

```html
<!-- a{click}+b{here} -->
<a href="">click</a><b>here</b>

<!-- a>{click}+b{here} -->
<a href="">click<b>here</b></a>
```

In second example the `<b>` element is placed *inside* `<a>` element. And that’s the difference: when `{text}` is written right after element, it doesn’t change parent context. Here’s more complex example showing why it is important:

```html
p>{Click }+a{here}+{ to continue}
```

...produces

```html
<p>Click <a href="">here</a> to continue</p>
```

In this example, to write `Click here to continue` inside `<p>` element we have explicitly move down the tree with `>` operator after `p`, but in case of `a` element we don’t have to, since we need `<a>` element with `here` word only, without changing parent context.

For comparison, here’s the same abbreviation written without child `>` operator:

```html
p{Click }+a{here}+{ to continue}
```

...produces

```html
<p>Click </p>
<a href="">here</a> to continue
```

## Notes on abbreviation formatting

<div class="note info">在元素和符号之间不需要空格。</div>

When you get familiar with Emmet’s abbreviations syntax, you may want to use some formatting to make your abbreviations more readable. For example, use spaces between elements and operators, like this:

```html
(header > ul.nav > li*5) + footer
```

But it won’t work, because space is a *stop symbol* where Emmet stops abbreviation parsing.

