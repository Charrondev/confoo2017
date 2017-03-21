## Life of a Pixel - Understanding Rendering Performance

#### From HTML to Pixels

Parsing HTML ->  Layout -> Painting -> Compositing

#### Let's Start with Pixels

Pixel = Tuple (red, green, blue)

In memory 3 * 3 pixels is layed out in memory as a 3*3*3 Matrix

#### Changing graphics

To move pixels you need to rewrite both the area where something is coming from and where it is going to. Need to figure out where all the pixels changing are which is expensive.

Alternative is Compositing. Instead gets treated at textures. Laying things out on top of each other.

#### GPU compositing bonuses

*All hardware accelerated. All of these things can be done in parallel very quickly ona GPU*

 * Change geometry of the texture
    * Scale
    * Rotate
* Change colors
    * grayscale
    * color swaps
* Change combinging colors
    * opacity
    * blending mode

#### Blending

How to combine the colors of overlapping textures?

`add, subtract, multiply, divide`

#### Summary

* Pixels are jsut emmory
* (Re)Painting means changing memory and is expensive
* GPUs are great at writing memory in parallel, CPUs not so much
* Paint textures once, then composite
* Compositing is a fast memory copy

### The browser rendering Pipeline

#### Different possible rendering paths

* *Worst Case*

    **Javascript -> Style -> Layout -> Paint -> Composite**

* *Better Case*

    **Javascript -> Style           -> Paint -> Composite**

* Best Case, CSS transforms fit here

    **Javascript -> Style                    -> Composite**

*"Performance is the art of avoiding work"*, **Paul Lewis**

#### Why does it paint?

* The renderer has no clue about the change
* Texture ("Layers") cost memory
* Layer creation is limited. Exceptions are.
    * `<video>` & `<canvas>`
    * 3d transforms: `transform: translate3d(x, y, z)`
    * `composite-only` animations
    * `will-change` property

#### What is composite-only

* Transform 3d
    * `translate`
    * `rotate`
    * `scale`
* Perspective
* Opacity*
* Cursor*
* Resize

⃰ Some browsers think differently

#### Browser Summary

* Layout and paint are expensive
* Compositing only when there is a layer
* layers have a cost, do not overuse!
* Check dev-tools to see when you will benefit from a layer
* Signals in CSS lead to layer creation
    * 3d transforms
    * will-change
    * composite-only animations
* Check out [CSS-Triggers](http://css-triggers.com)

### Canvas2d and WebGL

`<canvas>` is a layer...

Performance is ok, but gets poor as the number of objects scales. Uses javascript to paint to screen.

### What about WebGL?

* 3d API access to program the GPU directly (shaders)
* Much more verbose

FPS is much more stable with very high object counts

### Use the right tool

* **HTML and CSS**
    * Semantic & Accessible content
    * UI primitives
* **SVG**
    * Custom, responsive 2d shapes
    * Declarative animations
* **Canvas2d**
    * Custom 2d shapes & simple 2d graphics
* **WebGL**
    * Fully accelerated 2d graphics & 3d content
