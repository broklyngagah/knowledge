# dom
While most develoeprs have some understanding of how HTML and the DOM work,
there are a good amount of tags available that are most likely being misused. I
don't care about non-evergreen browsers, so that's the only guarantee about
compatibility I'm able to make.

## Tags
```txt
<nav>       the main navigation controls
<header>    the introductory block at the start of the page
<main>      the main content, should cover most of the page
<section>   the different parts of main
<footer>    page end, credits and stuff
<aside>     the sidebar, if any exists
```

## Events
A big gotcha of `dom` events it that they propegate to their parent nodes if left
unhandled. By setting `this.stopPropegation()` the events are no longer
propegated to their parents.

Another gotcha with the `dom`, is that when you're building dynamic systems
with JavaScript, existing dom nodes will have default behavior that is
executed. For example: when submitting a form, the default behavior is to
refresh the page after submission. To prevent this from happening you have to
use the `this.preventDefault()` method within the form element.

## Reflows & repaints
> A repaint occurs when changes are made to an elements skin that changes
> visibility, but do not affect its layout. Examples of this include outline,
> visibility, or background color. According to Opera, repaint is expensive
> because the browser must verify the visibility of all other nodes in the DOM
> tree.

> A reflow is even more critical to performance because it involves changes
> that affect the layout of a portion of the page (or the whole page).

- [source](http://stackoverflow.com/questions/2549296/whats-the-difference-between-reflow-and-repaint)
- [csstriggers.com](http://csstriggers.com/)

## Buttons
Creating a button can be done in multiple ways (all dependending on style).
Function comes down to semantics. Best practices for this are:
- __a__: use anchor tags for external links
- __button__: use buttons for all non-form related actions
- __input__: use input tags for all form related actions

[source](http://davidwalsh.name/html5-buttons)
