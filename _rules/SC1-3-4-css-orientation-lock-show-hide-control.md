---
name: CSS orientation lock
test_type: atomic

description: |
  This rule checks that a control on the page handle the content orientation.

success_criterion:
- 1.3.4 # Orientation

test_aspects:
- DOM Tree
- CSS Styling

authors:
- Jey Nandakumar
- Audrey Maniez
---

## Test Procedure

### Applicability

The rule applies to any content and functionnality that is visible and [included in the accessibility tree](#included-in-the-accessibility-tree) of any page that is not embedded in another page.

**Note**: Pages may be embedded inside other pages through elements such as iframes and object elements.

### Expectation

Each target element can be viewed and operationable in the user preferred orientation by activating a control in the page.

The user preferred orientation is either the device orientation or the orientation locked by the user in the device system settings.

## Assumptions

* This test assumes that a specific display orientation is not [essential](https://www.w3.org/TR/WCAG21/#dfn-essential), which is listed as a valid exception to SC 1.3.4. Examples where a particular display orientation may be essential are a bank check, a piano application, slides for a projector or television, or virtual reality content where binary display orientation is not applicable. 

## Accessibility support

*There are no major accessibility support issues known for this rule.*

## Background

- [Understanding Success Criterion 1.3.4: Orientation](https://www.w3.org/WAI/WCAG21/Understanding/orientation.html)

## Test Cases

### Passed

#### Passed example 1

A page is always displayed in landscape mode, whatever the device orientation is. A switch button on the page can be activated to displayed the page according to the device orientation. When activated, the switch button trigger the loading of an alternative CSS stylesheet that do not constraint the content orientation.

```html
<label for="orientation-unlocked">Unlocked orientation</label>
<input type="checkbox" id="orientation-unlocked" />
```

#### Passed example 2

A page contains a fonctionnality visible and usable only in landscape mode that disappears in portrait mode. A switch button on the page can be activated to show every fonctionnality in the page whatever the device orientation is.

### Failed

#### Failed example 1

A page is always displayed in landscape mode, whatever the device orientation is. A switch button on the page is identified has a control to displayed the page according to the device orientation, but the control is not functionnal.

```html
<!-- code -->
```
#### Failed example 2

A page contains a fonctionnality visible and usable only in landscape mode that disappears in portrait mode. There is no functionnality in the page to unlocked content orientation.

### Inapplicable

#### Inapplicable example 1

Content on the page can be viewed both in landscape and portrait mode.

#### Inapplicable example 2

A locked display orientation is essential to the content on the page. A piano web application requires the device to be in landscape mode to allow room for enough of the piano keys to be functionally usable. 