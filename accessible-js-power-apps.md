## Accessible Javascript-powered web applications

*by @imajolly at knowbility a W3C member*

### Misconceptions

* People with disabilities don't use the web
* Accessibility kills creativity
* JavaScript isn't accessible
* Accessibility costs to much

### What is accessibility?

**W3C WAI**: Web accessibility means that people with disabilities can use the Web.


#### Key A11Y Principles

* Perceivable
* Operable
* Understandable
* Robust

#### Detecting issues

* Browser tools
* Keyboards: Try navigating with just keyboard
* Screen Readers
    * **Mac**: VoiceOver (Safari, Chrome)
    * **Windows**: JAWS (IE) NVDA (Firefox)

#### Tools

* **Angular**: ngAria
* **React**: react-a11y
* **vanilla**: a11y.js

### P.O.U.R.

**P**: Perceivable
* Alt text
* On-screen Notices, use `aria-live` to inform of changes
* Focus Management

**O**: Operable
* Can peoples use your app without a mouse? With their voice? Without sight?
* Use semantic HTML whenever possible
* `<div>` || `<span>` !== `<button>`
* ARIA, please!
    * Don't overuse ARIA attributes
    * If you can use a native HTML element or attribute with the semantics and behaviour you require already built in, instead of repurposing an element and adding an ARIA role, state, or property to make it accessible, then do so.
* Be zealous about focus management
    * **Forms**: error reporting/handling
    * **Modals**: set focus, return it properly afterwards
    * **Dynamic Content**: set focus to new content as needed

**Robust**
* Ensure your app can work with a wide variety of browsers and assistive technologies
* Progressive enhancement is a good practice. That or server-side rendering
* Parsing: validate your code! Especially W3C validator. Checks for invalid ARIA attributes.

#### Good example
* Web Experience Toolkits
* Government of Canada
* Healthcare.gov
