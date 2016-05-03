# CSS Code Checklist

## 1. Are nested selectors unnecessarily increasing specificity?
Why do

```css
.selector-a .selector-b .selector-c {}
```
when

```css
.selector-b .selector-c {}
```
or even

```css
.selector-c {}
```
works?

## 2. Are nested selectors breaking readability?
```sass
.selector-a {
	.selector-b {}
	.selector-c {}
}

.selector-d {
	// ...
}

// ...
```
Makes sense.

```sass
.selector-a {
	.selector-b {}
	.selector-c {}
	.selector-e {}

	// ...

	// ...

	// ...

	// PAGE DOWN is hit 5 more times

	.selector-f {}

	// Oops, you missed .selector-f {}
}
```
Does not make sense. Instead, break down the nesting:

```sass
.selector-a {
	// .selector-a styles
}
.selector-a .selector-b {}
.selector-a .selector-c {}
.selector-a .selector-e {}
.selector-a .selector-f {}
```

## 3. Are `:pseudo-selectors` unnecessarily increasing specificity (BY A LOT)?
Not ok:

```sass
.selector-a:not(:last-of-type) {}
```

OK:

```sass
.selector-a__element--or-modifier::last-child {} // Read up on BEM naming convention
```

## 4. Can you prototype another view using the given styles (Is it reusable)?
This applies more towards reusable components than single-use features.

## 5. Are there browser concerns?

## 6. Are tag names part of the selector?
If so, remove them.

## Links
[https://css-tricks.com/what-a-css-code-review-might-look-like/](CSSTricks: What a CSS Code Review Might Look Like)
