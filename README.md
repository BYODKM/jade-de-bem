# jade-de-bem

> Jade Mixins for the Rapid BEM Coding

## Usage

```jade
include jade-de-bem

+div(class="block --special")
  +ul(class="__items foo")
    +li(class="__item --new foo bar")
      +a(class="__link baz")
        | Foo
```

1. Include the `jade-de-bem` mixin.
2. Follow the class rules. See the [specification](#specification).
3. That's it.

### Yields:

```html
<div class="block block--special">
  <ul class="block__items foo">
    <li class="block__item block__item--new foo bar">
      <a class="block__link baz">Foo
      </a>
    </li>
  </ul>
</div>
```

## Install jade-de-bem

- `$ bower install jade-de-bem`
- or download [master.zip](https://github.com/internets-inc/jade-de-bem/archive/master.zip)

## Specification

Start with `+` sign and keep the className order.

```jade
+E(class="(block|__element|--modifier__element) [--modifier] [else]")
```

### Separators Configuration

https://github.com/internets-inc/jade-de-bem/blob/master/lib/bem.jade#L5-L6

```jade
config.element  = '__'
config.modifier = '--'
```

### Terminal Indicator

Unfortunately, you need to terminate child scopes when you have them.

```jade
+bem(false)
```

Use like this:

```jade
+div(class="parent")
  +header(class="__header")
  +div(class="__main")
    +div(class="child")
      +ul(class="__items")
        +li(class="__item")
          +bem(false)
  +footer(class="__footer")
```

Yields:

```html
<div class="parent">
  <header class="parent__header">
  </header>
  <div class="parent__main">
    <div class="child">
      <ul class="child__items">
        <li class="child__item">
        </li>
      </ul>
    </div>
  </div>
  <footer class="parent__footer">
  </footer>
</div>
```

## License

MIT
