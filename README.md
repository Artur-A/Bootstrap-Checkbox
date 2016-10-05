# Bootstrap-Checkbox

This is a simple customization for bootstrap checkbox. Only _pure CSS_ is used.
With a few modifications it also can be applied for a custom checkbox without using Bootstrap.

## Demo
Check online [example in JSFiddle](https://jsfiddle.net/hw8nuxz4/2/)

![Bootstrap Checkbox](https://wtf.jpg.wtf/e7/ab/1475666428-e7aba580c18be9ee7340a0542936b9e5.png)

## How to use
To apply custom checkbox you only need to add `.checkbox-bootstrap` class and 
`<span class="checkbox-placeholder"></span>` to usual Bootstrap checkbox implementation.

```html
<div class="checkbox">
      <label class="checkbox-bootstrap">                                        
          <input type="checkbox">             
          <span class="checkbox-placeholder"></span>           
          Original checkbox
      </label>
 </div>
```
Similar for an inline checkbox:
```html
<label class="checkbox-inline checkbox-bootstrap">
  <input type="checkbox">
  <span class="checkbox-placeholder"></span>
  Inline 
</label>
```
To inhance the size just add `.checkbox-lg` class:
```html
<div class="checkbox">
      <label class="checkbox-bootstrap checkbox-lg">                           
          <input type="checkbox">             
          <span class="checkbox-placeholder"></span>           
          Large checkbox unchecked
      </label>
 </div>
```

## Browser support
__IE__: 10+

__Chrome, Firefox, Safari, Opera__: last 2 stable versions (probably much older).

For IE <= 9 or the rest old browsers that does not support some features the system will fallback to an original browser checkbox.
For instance, IE 8 and IE 9 displays next image:

![IE fallback](https://wtf.jpg.wtf/dc/71/1475666615-dc716b4b777dd960c4d5844ae6800454.png)

## How it works
There are two main techniques used for CSS based on the MDN article [Advanced styling for HTML forms](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/Advanced_styling_for_HTML_forms).

* __Label redirects a click event__

    Label can redirect a click event to its target if it has `for` attribute like `<label for="target_id">Text</label> <input id="target_id" type="checkbox" />`, or if it contains input as in Bootstrap case: `<label><input type="checkbox" />Text</label>`.

    It means that it is possible to place label in one corner of the browser, click on it, and then label will redirect click event to the checkbox located in other corner.

    In this particular case we hide original checkbox visually, but make it still working and taking click event from label.
    In the label itself we emulate checkbox with `<span>` tag.

* __General non supported tag for old browsers__

    Some old browsers does not support several CSS features like selecting siblings `p+p` or specific search `input[type=checkbox]`.
    According to the MDN article browsers that support these features also support `:root` CSS selector, while others not. The `:root` selector just selects the root element of a document, which is `html` in a HTML page.
    Thus it is possible to use `:root` for a fallback to old brosers and original checkboxes.


## License
Apache License 2.0