---
layout: default
title: JTooltip by Jamie Tsao
---

### Introduction
JTooltip is a lightweight, easy to use jQuery library for creating tooltips.  The tooltip can appear above, below, to the right, or to the left of the target element.

<div class="example_row">
  <span class="tooltip_target" id="intro-1" data-jtooltip="UP">UP</span>
  <span class="tooltip_target" id="intro-2" data-jtooltip="DOWN">DOWN</span>
  <span class="tooltip_target" id="intro-3" data-jtooltip="RIGHT">LEFT</span>
  <span class="tooltip_target" id="intro-4" data-jtooltip="RIGHT">LEFT</span>
  <span class="tooltip_target" id="intro-5" data-jtooltip="A">B</span>
  <span class="tooltip_target" id="intro-6" data-jtooltip="START">SELECT</span>
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
<span id="foo" title="From the 'title' attribute">Foo</span>
<span id="bar" data-jtooltip="From the 'data-jtooltip' attribute">Bar</span>
```
```javascript
$(document).ready(function() {
    JTooltip.create({ target : "#foo" });
    JTooltip.create({ target : "#bar", contentAttr : "data-jtooltip" });
});
```

<div class="example_row">
    <span class="tooltip_target" id="foo" title="From the 'title' attribute">Foo</span>
    <span class="tooltip_target" id="bar" data-jtooltip="From the 'data-jtooltip' attribute">Bar</span>
</div>

Other configuration options include the ability to hide the stem, customize the offset position, and animate the display of the toolip:

```javascript
$(document).ready(function() {
    // multiple tooltips can be created with a single 
    // invocation by using a class selector
    JTooltip.create({ 
                      target : ".e_top",
                      contentAttr : "data-jtooltip",
                      position: "top",
                      stem : false,
                      offset : { x : 0, y : -5 },
                      animateShow : true
                    });
                    
    JTooltip.create({ 
                      target : ".e_bottom",
                      contentAttr : "data-jtooltip",
                      position: "bottom",
                      stem : false,
                      offset : { x : 0, y : 5 },
                      animateShow : true
                    });

});
```

<div class="example_row">
    <span class="span_3 emoticon e_top" data-jtooltip="cat">:cat:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="dog">:dog:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="mouse">:mouse:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="hamster">:hamster:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="rabbit">:rabbit:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="wolf">:wolf:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="frog">:frog:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="tiger">:tiger:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="koala">:koala:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="bear">:bear:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="pig">:pig:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="cow">:cow:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="boar">:boar:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="monkey">:monkey_face:</span>
    <span class="span_3 emoticon e_top" data-jtooltip="horse">:horse:</span>
</div>
<div class="example_row">
    <span class="span_3 emoticon e_bottom" data-jtooltip="camel">:camel:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="sheep">:sheep:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="elephant">:elephant:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="panda">:panda_face:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="snake">:snake:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="bird">:bird:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="chicken">:chicken:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="turtle">:turtle:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="ant">:ant:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="fish">:fish:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="octopus">:octopus:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="snail">:snail:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="whale">:whale:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="dolphin">:dolphin:</span>
    <span class="span_3 emoticon e_bottom" data-jtooltip="crocodile">:crocodile:</span>
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
        JTooltip.create({ target : "#intro-1", contentAttr : "data-jtooltip", position: "top" });
        JTooltip.create({ target : "#intro-2", contentAttr : "data-jtooltip", position: "bottom" });
        JTooltip.create({ target : "#intro-3", contentAttr : "data-jtooltip", position: "right" });
        JTooltip.create({ target : "#intro-4", contentAttr : "data-jtooltip", position: "right" });
        JTooltip.create({ target : "#intro-5", contentAttr : "data-jtooltip", position: "left" });
        JTooltip.create({ target : "#intro-6", contentAttr : "data-jtooltip", position: "left" });
        // examples for 'Simple to Use'
        var jqObj = $('#jingle-2');
        var ele = document.getElementById('jingle-3');

        JTooltip.create({ target : "#jingle-1", content: "Bells" });
        JTooltip.create({ target : jqObj, content: "Bells" });
        JTooltip.create({ target : ele, content: "All The Way!" });

        JTooltip.create({ target : "#foo" });
        JTooltip.create({ target : "#bar", contentAttr : "data-jtooltip" });

        JTooltip.create({ target : ".e_top", contentAttr : "data-jtooltip", position: "top", stem : false, offset : { x : 0, y : -5 }, animateShow : true });
        JTooltip.create({ target : ".e_bottom", contentAttr : "data-jtooltip", position: "bottom", stem : false, offset : { x : 0, y : 5 }, animateShow : true });

    });
</script>