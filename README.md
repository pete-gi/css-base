# Petegi's CSS Base

My custom base for working with CSS. No dependencies included.

Mains focus was Reset and Custom Properties.
Custom Properties that are used by Reset and can be used by Container Style Queries (instead of Media Queries).

Everything should be used as one, although tokens (custom properties), reset and utils are available to be imported on their own.

The default export is `all`.

## Instalation

The package is on npm as `@petegi/css-base`. If you don't know how to install it without instructions, then don't. Use different package.

It's not to be used by other people and can be deleted in the future.

## Reset

It's using custom properties which are described a bit below, but it's necessary to say it:
**Base Font Size is defined to have 62.5% which is equivalent to 10px**.
Keep it in mind as I'm using mainly `rem` values.

And what to say about reset - it's a mix of `normalize` (everyone knows it), `ress` (my personal favourite for a few years) and some popular internet peoples ideas.
Having `allow-discrete` for animating from `display: none`, or `navigation: auto` for view transitions by default it quite nice.
It doesn't include anything for IE.

Popovers and dialogs have some basic styling for appearing on the screen - thanks to mentioned `allow-discrete` and `@starting-style` at-rule.

Oh and if you're using it, remember to use `box-sizing` property when setting padding on elements. This reset comes with browser-default `content-box` value.

## Custom Properties

Almost all of the properties are defined as `@property` so they can be animated easily.
The only ones that are not, are breakpoints.

### Color

Almost all colors have the same structure:

```
--color-primary
--color-primary-light
--color-primary-dark
```

Light/Dark version are computed automatically with `---color-modifier`.

Each has also transparent (0.5) version:

```
--color-primary-transparent
--color-primary-light-transparent
--color-primary-dark-transparent
```

The only color properties that don't have light/dark versions are `--color-transparent` and `--color-shadow`.

One more thing - Text and Background colors are automatically applied to current Color Scheme.
Since it's not really good to have them with light/dark modifiers, they have up/down modifiers.

```
--color-text-up (#fff)
--color-text (#eee)
--color-text-down (#ddd)
```

There are also `--color-black` and `--color-white`. That's it.

### Font

Default `--font-family` is `system-ui`. Only one font property is available.

Weights have modifiers for `-light`, `-regular` and `-bold`.

Sizes and Line Heights have a bit more modifiers:

```
--font-size-xs
--font-size-sm
--font-size-md
--font-size-lg
--font-size-xl

--line-height-xs
--line-height-sm
--line-height-md
--line-height-lg
--line-height-xl
```

### Border

```
// Single values
--border-width
--border-width-bold

--border-radius-xs
--border-radius-sm
--border-radius-md
--border-radius-lg
--border-radius-xl

--border-radius-circle

// These are the only "full" ones
--border-solid
--border-dashed
```

### Duration

Duration varies from `xs` (0.1s) to `xl` (0.5s). Naming convention from sizing is not quite fair here, but it's easier to remember.

If a user prefers reduced motion, all duration properties are defined to have `0s`.

### Shadow

Shadow has 3 versions and each of it has 5 modifiers. So we have:

```
--shadow-{xs-xl}
--shadow-top-{xs-xl}
--shadow-bottom-{xs-xl}
```

### Size

```
--size-xs: 0.25rem;
--size-sm: 0.5rem;
--size-md: 1rem;
--size-lg: 2rem;
--size-xl: 3rem;
--size-2xl: 4rem;
--size-3xl: 5rem;
```

### Spacing

```
--space-xxs: 0.25rem;
--space-xs: 0.5rem;
--space-sm: 0.75rem;
--space-md: 1rem;
--space-lg: 1.5rem;
--space-xl: 2rem;
--space-auto: auto;
```

### Breakpoints

A set of boolean values that can be used as Container Style Queries until we have `@custom-media`.
Media Queries that are used to properly set these values are writted using `rem` units, to they have effect on zoomed in/out display.
Quite good thing to know is `rem` units in `@media` queries definitions have always base browser value - they do not get they root value from `html` or `:root` elements `font-size`.

Below is a list of `px` values that match screen sizes.

```
--xs-down <= 500px
--xs-up > 500px

--sm-down <= 800px
--sm-up > 800px

--md-down <= 1200px
--md-up > 1200px

--lg-down <= 1600px
--lg-up > 1600px

--xl-down <= 2000px
--xl-up > 2000px
```

#### Usage

Notice the container name here. It's defined on `html` element in the reset.

```
@container root style(--sm-up: true) {
  /* Your styles */
}
```
