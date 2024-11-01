2024-11-01 22:12

Tags: [[Frontend]] [[Animation]] [[JS]] [[CSS]]

---

## Set a style variables that can be used in CSS:

In JS:

```js
document.body.style.setProperty(property, value);
// document.body.style.setProperty('--header-height', '2rem');
```

In CSS:

```css
max-height: var(property)
// max-height: var(--header-height) ~ max-height: 2rem
```

## Pause animation and control delay by variable
```css
animation: rotate 1s linear infinite;
animation-play-state: paused;
animation-delay: calc(var(--scroll) * -1s);
animation-iteration-count: 1;
animation-fill-mode: both;
```


---
# References