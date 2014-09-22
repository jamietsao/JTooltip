---
layout: default
title: JTooltip by Jamie Tsao
---

### Introduction
JTooltip is a lightweight, easy to use jQuery library for creating tooltips.  The tooltip can appear above, below, to the right, or to the left of the target element.

<div class="example_row">
  <span class="tooltip_target" id="intro-1" data-tooltip="UP">UP</span>
  <span class="tooltip_target" id="intro-2" data-tooltip="DOWN">DOWN</span>
  <span class="tooltip_target" id="intro-3" data-tooltip="RIGHT">LEFT</span>
  <span class="tooltip_target" id="intro-4" data-tooltip="RIGHT">LEFT</span>
  <span class="tooltip_target" id="intro-5" data-tooltip="A">B</span>
  <span class="tooltip_target" id="intro-6" data-tooltip="START">SELECT</span>
</div>

### Simple to Use
You create tooltips for any 'target' by calling `JTooltip.create` with a CSS selector/jQuery object/DOM element, and the content for the tooltip.

```html
<span class="tooltip_target" id="jingle-1">Jingle</span>
<span class="tooltip_target" id="jingle-2">Jingle</span>
<span class="tooltip_target" id="jingle-3">Jingle</span>
```
```javascript
var jqObj = $('#jingle-2');
var ele = document.getElementById('jingle-3');

JTooltip.create({ target : "#jingle-1", content: "Bells" });
JTooltip.create({ target : jqObj, content: "Bells" });
JTooltip.create({ target : ele, content: "All The Way!" });
```

<div class="example_row">
  <span class="tooltip_target" id="jingle-1">Jingle</span>
  <span class="tooltip_target" id="jingle-2">Jingle</span>
  <span class="tooltip_target" id="jingle-3">Jingle</span>
</div>

Text from the `title` attribute can be used as content by not including the `content` option (use the `contentAttr` option to specify an attribute other than `title`).

```html
<span class="my-tooltip" title="Text from the 'title' attribute">Foo</span>
<span class="my-tooltip" title="Allows for content re-use">Bar</span>
```
```javascript
$(document).ready(function() {
    // multiple tooltips can be created with a single 
    // invocation by using a class selector
    JTooltip.create({ target : ".my-tooltip" });
});
```

<div class="example_row">
    <span class="tooltip_target my-tooltip" id="4" title="Text from the 'title' attribute">Foo</span>
    <span class="tooltip_target my-tooltip" id="5" title="Allows for content re-use">Bar</span>
</div>

### Configuration Options
JTooltip can be customized by overriding default configuration options.  `JTooltip.create` expects an `options` object.  `target` is the only required option.

Option Name | Description
----------- | :------------
target | Target that triggers the tooltip when moused over. This can be a CSS selector, jQuery object, or DOM element. **This option is required.** 
content | Content displayed in the tooltip. This can be a string, an object, or a function that evaluates to a string or object.  If not specified, the content is taken from the `title` attribute (use `contentAttr` to specify a different attribute) of the target.
contentAttr | If `content` is not set, this option can be used to specify an attribute other than `title` to use as the content.
position | Position of the tooltip relative to the target. Options are `top` **(default)**, `right`, `bottom`, and `left`.
offset | Offset (in pixels) where the tooltip should appear, relative to the target.  Specified as an object with x & y properties (e.g. `{ x : 0, y : 10 }`).  Default is 5 pixels to the top/right/bottom/left (depending on `position`) of the target.
showDelay | Delay (in milliseconds) before the tooltip appears after mousing over the target.  Default is 100 milliseconds.
hideDelay | Delay (in milliseconds) before the tooltip disappears after mousing away from the target (and tooltip).  Default is 75 milliseconds.
animateShow | Indicates whether (true) or not (false) to animate the display of the tooltip.  Default is false.
animateDur | The duration (in milliseconds) of the tooltip animation (if `animateShow` is true).
stem | Indicates whether (true) or not (false) to include a stem for the tooltip bubble.  Default is true.
maxWidth | Maximum width (in pixels) of the tooltip.  Default is 300 pixels.


### Usage
To start using JTooltip, simply include jQuery and the JTooltip javascript and css files.

```html
<link rel="stylesheet" type="text/css" href="jtooltip.css" />
<script src="jquery.min.js"></script>
<script src="tooltip.js"></script>
```

### Issues and Enhancements
Find a bug?  Would like to request an enhancement?  Please log it <a href="https://github.com/jamietsao/JTooltip/issues" target="_blank">here</a>.


<script tyoe="text/javascript">
    $(document).ready(function() {
        // Examples from Introduction
        JTooltip.create({ target : "#intro-1", contentAttr : "data-tooltip", position: "top" });
        JTooltip.create({ target : "#intro-2", contentAttr : "data-tooltip", position: "bottom" });
        JTooltip.create({ target : "#intro-3", contentAttr : "data-tooltip", position: "right" });
        JTooltip.create({ target : "#intro-4", contentAttr : "data-tooltip", position: "right" });
        JTooltip.create({ target : "#intro-5", contentAttr : "data-tooltip", position: "left" });
        JTooltip.create({ target : "#intro-6", contentAttr : "data-tooltip", position: "left" });
        // examples for 'Simple to Use'
        var jqObj = $('#jingle-2');
        var ele = document.getElementById('jingle-3');

        JTooltip.create({ target : "#jingle-1", content: "Bells" });
        JTooltip.create({ target : jqObj, content: "Bells" });
        JTooltip.create({ target : ele, content: "All The Way!" });

        JTooltip.create({ target : ".my-tooltip" });       
    });
</script>