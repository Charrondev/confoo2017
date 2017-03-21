## Getting SVGs up and running

*by Sarah Etter*

#### What is SVG?
* Scalable Vector Graphic
* XML
* Built from geometrical primitives

#### Why SVG?
* Scalable!
* High fidelity
* resolution Independant
* Small file sizes
* script-able
* Animate-able
* quick to modify
* Semantic
* Accessible

#### How to create SVG
* Hand code
* Vector imaging program
    * Illustrator
    * Inkscape
    * Sketch

#### Hot to use in webpage
* Inline SVG
    * Doesn't actually have to be in one line
    * Place directly into the page
    * Remove an HTTP request
    * Can be manipulated in the DOM just like HTML using JS or CSS
* CSS `background`
* `<img>` tag. No access to manipulate the SVG
* You can but you shouldn't
    * `<object>`
    * `<embed>` not part of the spec
    * `<iframe`

### SVG Coordinate System
* Viewport
    * set by `height` and `width` properties
    * anything outside of the viewport is clipped
* viewBox
    * `<svg viewBox="0 0 200 200" />` viewBox="originX originY endX endY"
    * If the viewBox is the same as the Viewport than it maps 1unit -> 1 px
    * if viewBox is set to 50 and Viewport 200 than 1 unit -> 4px

### Elements
#### Circle
`<circle cx="100" cy="100" r="50" fill="#fff" />`
<svg>
    <circle cx="100" cy="100" r="50" fill="#fff" />
</svg>

#### Ellipse
`<ellipse cx="100" cy="100" rx="50" ry="100" fill="#fff" />`

<svg>
    <ellipse cx="100" cy="100" rx="50" ry="100" fill="#fff" />
</svg>

#### Rectabgle
`<rect x="0" y="0" rx="50" ry="100" fill="#fff" />`

<svg height="100" width="500">
    <rect width="400" height="100" fill="#fff" />
</svg>

#### Line
`<line x1="0" x2="100" y1="50" y2="100" stroke-width="1" stroke="#fff" />`
<svg height="100" width="500">
    <line x1="0" x2="100" y1="50" y2="100" stroke-width="1" stroke="#fff" />
</svg>

#### Polyline
`<polyline fill="none" stroke="black" 
      points="20,100 40,60 70,80 100,20"/>`

<svg height="100" width="400">
    <polyline fill="none" stroke="white" 
        points="20,100 40,60 70,80 100,20"/>
</svg>

#### Text
*Text is positioned from bottom left*
`<text x="10" y="50" fill="#af1414">Hello World</text>`

<svg>
    <text x="10" y="50" fill="#af1414">Hello World</text>
</svg>

#### Polygony
<svg>

</svg>
`<polygon points="0,10 30,50" fill="#fff>`

#### Path
<svg height="100" width="100">

</svg>
`<path d="Mgibberishgibberishgibbersih" fill="#fff">`

#### Group
<svg>

</svg>
`<g transform="translateY(-50px)"></g>`

#### Symbol
<svg>

</svg>
`<symbol id="phone" viewBox="0 0 200 200">`

`<use xmls:link="phone">`

#### Gradient

#### SVG patterns / Image Patterns

### Responsive

* max-width: 100%; doesn't work;
* trick
    * Put a div container around the SVG    
    * Put rest of trick here later

### Styling SVG
* fill
* stroke
* stroke-width:
* stroke-linecap
* stroke-dasharray - how wide dashes are
* stroke-dashoffset - how much space between dashs // Animating this amkes it look like its drawing.


### Optimizing SVG code
* Remove custom attributes
* Remove doctype
* add semantic classes, if this wasn't done in the graphics program (name of layer is usually added as the class)
* Check shapes, if something is a circle, then it should be a circle tag, not a huge path. Sometimes things are weird
* [SVG Optimizer](http://petercollingridge.appspot.com/svg-optimiser)

### Browser Support
* Everything!!! (except IE8 and very old android)

### Accessibility
* `<title>` element
* `<desc>` element

## Animation

#### CSS Keyframes
[Example 1](http://codepen.io/sarahetter/pen/NNXGoO)

#### CSS Transition
[Example 1](http://codepen.io/sarahetter/pen/QNQPgz)

#### Snap.svg
[Example 1](http://codepen.io/sarahetter/pen/VayQaV)

#### Greensock
[Example 1](http://codepen.io/sarahetter/pen/vxgmxp), [Example 2](http://codepen.io/sarahetter/pen/EWZwLZ), [Example 3](http://codepen.io/nsayenko/details/BpdzOZ)