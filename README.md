# FitText.js, a <del>jQuery plugin</del> tiny script for inflating web type
FitText makes font-sizes flexible. Use this <del>plugin</del> script on your fluid or responsive layout to achieve scalable headlines that fill the width of a parent element.

## How it works
If you have a small site and don't want to attach jQuery, just attach fittext.js and put this just before `</body>` (responsive_headline is an header id).
```html
<script>
  window.fitText( document.getElementById("responsive_headline") );
</script>
```
### The Compressor
The default setting works pretty well, but when it doesn't FitText has one setting you can adjust. If your text resizes poorly or is resizing all hurdy gurdy, you'll want to turn tweak up/down the compressor. It works a little like a guitar amp.
```html
window.fitText( document.getElementById("responsive_headline"), 1.2 ); // turn the compressor up (font will shrink a bit more aggressively)
window.fitText( document.getElementById("responsive_headline"), 0.8 ); // turn the compressor down (font will shrink less aggressively)
```
This will hopefully give you a level of "control" that might not be pixel perfect, but scales smoothly & nicely.

### Custom resizer function
The resize function can be configured if needed. To use an alternative resize function, provide a function that returns the intended resize function as the `resizer` option.

For example:
```html
var createResizer = function(el, compressor, options) {
    return function() {
        // This is the default resizer function, for example
        el.style.fontSize = Math.max(Math.min(el.clientWidth / (compressor*10), parseFloat(settings.maxFontSize)), parseFloat(settings.minFontSize)) + 'px';
    }
}
window.fitText( document.getElementById("responsive_headline"), null, { resizer: createResizer });
```
In this example, the createResizer function will be invoked to prepare the returned function for use. Then, any time the resizing is to be performed, the new function will be used instead of the default.

### Thanks
Thanks to Trent, Dave and Reagan for original FitText.js: https://github.com/davatron5000/FitText.js
http://fittextjs.com/
