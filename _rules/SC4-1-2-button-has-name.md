---
name: Buttons have an accessible name

description: |
  Each button element has an accessible name

success_criterion:
- 4.1.2

test_aspects:
- DOM Tree
- CSS Styling

authors:
- Wilco Fiers
- Stein Erik Skotkjerra
---

## Test procedure

### Applicability

The rule applies to elements that are [visible on the page](#visible-on-the-page) or [exposed to assistive technologies](#exposed-to-assistive-technologies) with the [semantic role](#semantic-role) of `button`, except for `input` elements of `type="image"`.

### Expectation

Each target element has an [accessible name](#accessible-name) that is [non-empty](#non-empty)

## Assumptions

- The rule assumes that all buttons are user interface components as defined by WCAG 2.

## Accessibility Support

There are no major accessibility support issues known for this rule.

## Background

- [https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html)
- [https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=412#qr-ensure-compat-rsv](https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=412#qr-ensure-compat-rsv)
- [ARIA14: Using aria-label to provide an invisible label where a visible label cannot be used](https://www.w3.org/TR/WCAG20-TECHS/ARIA14.html)
- [https://www.w3.org/TR/WCAG20-TECHS/ARIA16.html](https://www.w3.org/TR/WCAG20-TECHS/ARIA16.html)

## Test cases

### Passed

#### Pass example 1

Regular button.

```html
<button>My button</button>
```

#### Pass example 2

Value attribute as the accessible name.

```html
<input type="submit" value="Submit">
```

#### Pass example 3

`aria-label` for the accessible name.

```html
<button aria-label="My button"></button>
```

#### Pass example 4

Span tag with role button and has name defined by aria-label.

```html
<span role="button" aria-label="My button"></button>
```

#### Pass example 5

Summary element has a default semantic role of button.
```html
<summary>Press Here</summary>
```

#### Pass example 6

Disabled elements are also applicable.

```html
<button disabled>Delete</button>
```

#### Pass example 7

Off screen elements should be tested.

```html
<html>
  <style>
    .notInPage {
      position: absolute;
      left: -9999px;
      top: -9999px;
    }
  </style>
  <body>
    <button data-rule-target class='notInPage'>Save</button>
  </body>
</html>
```

### Failed

#### Fail example 1

Value attribute does NOT give an accessible name, only for input elements.

```html
<button type="button" value="read more"></button>
```

#### Fail example 2

`aria-hidden` buttons should be tested.

```html
<button aria-hidden="true"></button>
```

#### Fail example 3

Span tag with role button with no name.

```html
<span role="button"></span>
```

#### Fail example 4

Off screen element with out an accessible name.

```html
<html>
  <style>
    .notInPage {
      position: absolute;
      left: -9999px;
      top: -9999px;
    }
  </style>
  <body>
    <button data-rule-target class='notInPage' value='delete'></button>
  </body>
</html>
```

### Inapplicable

#### Inapplicable example 1

Image buttons are tested in a different rule

```html
<input type='image' value='download'>
```

#### Inapplicable example 2

Not visible in page and not exposed to assistive technologies.

```html
<html>
  <style>
    .notInPage {
      position: absolute;
      left: -9999px;
      top: -9999px;
    }
  </style>
  <body>
    <button data-rule-target class='notInPage' aria-hidden='true'>Confirm</button>
  </body>
</html>
```

#### Inapplicable example 3

Inapplicable: role overridden to link for button element.

```html
<button role='link'>take me somewhere</button>
```
