# :roots naming conventions

> This convention is very close to SUIT. Please refer to the [SUIT naming conventions](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md) for more details. One major difference is that modifiers use state (`is-`) classes.

  ```css
.Button { /* ComponentName */ }
.Button.is-primary { /* ComponentName.is-modifierOfComponent */ }

.Nav { /* ComponentName */ }
.Nav-item { /* ComponentName-descendentName */ }
.Nav-item.is-selected { /* ComponentName-descendentName.is-stateOfComponent */ }

.u-fullWidth { /* u-utilityName */ }
```





## ComponentName

The component's name must be written in PascalCase. This makes it stand out and it's easier to spot in the markup as well in style sheets.

```html
<nav class="Nav"></nav>
<main class="Main"></main>
<footer class="TabBar"></footer>
```

```css
.Nav { /* … */ }
.Main { /* … */ }
.TabBar { /* … */ }
```





## ComponentName-descendentName

If a component has child elements, the class name starts with the `ComponentName`, followed by `-descendentName`. Descendent names must be
written in camelCase.

```html
<nav class="Nav">

  <button class="Nav-item">
    <span class="Nav-textLabel"></span>
  </button>

  <button class="Nav-item">
    <span class="Nav-textLabel"></span>
  </button>

</nav>
```

```css
.Nav { /* … */ }
.Nav-item { /* … */ }
.Nav-textLabel { /* … */ }
```





## ComponentName.is-state/modifier

If a Component or Component-descendent has different modifiers (versions) or states, use  `is-modifierName` or `is-stateName`. They must be written in camelCase.

```html
<button class="Nav-item is-primary"></button>
<button class="Nav-item is-small"></button>
<button class="Nav-item is-small is-selected"></button>
```

```css
.Nav-item.is-primary { /* … */ }
.Nav-item.is-small { /* … */ }
.Nav-item.is-selected { /* … */ }
```

**Note: Never style these classes directly; they should always be
used as an adjoining class.**

This means that the same modifier and state names can be used in multiple places, but every component must define its own styles (as they are scoped to the component).





## u-utilityName

Utility classes have mostly just a single purpose and can be applied directly to any element. They must use a camelCase name.

```html
<nav class="Nav u-fullWidth">
  <button class="Nav-item u-fullWidth"></button>
  <button class="Nav-item"></button>
  <button class="Nav-item u-alighRight"></button>
</nav>
```

```css
.u-fullWidth { /* … */ }
.u-alighRight { /* … */ }
```

Note that unlike modifiers and states, utility classes are used globally and therfore don't need to be tied to a Component.





## js-selectorName

Don't use Component classes to select elements with JavaScript, add a `js-selectorName` class instead. Or using an attribute is fine too, especially when dictated by the JS framework.

```html
<button class="Nav-item js-tab"></button>
<button class="Nav-item js-downloadButton"></button>
<button class="Nav-item" framework="nav-item"></button>
<button class="Nav-item" el-nav-item></button>
```

This separation makes it easier to rename/refactor Components without worring about breaking functionality.
