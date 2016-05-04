# React

This section covers the basics of [React](https://facebook.github.io/react/index.html). React operates as the
view in Untangled's MVC architecture, so understanding it's behavior will help tremendously when building your web app's
UI.

## Virtual DOM

Firstly, if you are not familiar with the real DOM, [this is an excellent and brief primer](https://css-tricks.com/dom/).

When standard Javascript modifies the DOM, the new DOM has to be rendered to HTML and displayed in the browser.
It turns out that rendering the DOM to HTML is expensive, because [it was not originally designed for the complex web
apps that we use today](http://tonyfreed.com/blog/what_is_virtual_dom). Thus, large web-apps that frequently modify the
DOM can quickly become sluggish performance-wise.

How does React solve this rendering performance issue? Even though rendering the DOM is an expensive operation, browsers
have become exceptionally efficient at interpreting Javascript. React was built to minimize modifications to the DOM, so
that rendering to HTML is as efficient as possible.

React minimizes DOM modifications by doing what computer scientists do best – adding another layer of abstraction.
Standard Javascript directly renders the DOM to HTML. React, by contrast, does not want you to modify the DOM. Instead,
you create React Elements and Components that form the Virtual DOM -- a lightweight, javascript representation of the DOM.

When you change the elements and components in React's virtual DOM, React executes a 'Virtual DOM Diff' to determine
what changed between the old virtual DOM and the new virtual DOM. This is a very fast operation because it is still
occurring in Javascript land, the real DOM is not yet involved. Once React has determined exactly what needs to change
and what needs to stay the same, it batches the virtual DOM changes and applies them to the real DOM, which is then
rendered to HTML.

So, by keeping track of desired changes to the DOM within Javascript, and batch applying the fewest changes necessary to
reflect the web app's changing state, the browser renders fewer changes to the DOM and does so less frequently than
repeated calls to the browser's slower DOM manipulation functions.

There are [plenty of resources](#more) that discuss virtual dom in more depth.

## The `key` attribute

## Props and Component Local State

## UI Render Lifecycle

TODO: More info here

For more information, see the [React docs on Lifecycle Methods](https://facebook.github.io/react/docs/component-specs.html#lifecycle-methods).

## <a name="more"></a>Additional Material

For those who are interested in learning more about React, I recommend looking at:

- [Thinking in React](https://facebook.github.io/react/docs/thinking-in-react.html), an excellent and concise primer on
how React UIs are intended to be designed.
- [React (Virtual) DOM Terminology](https://facebook.github.io/react/docs/glossary.html)
- [React.js Tutorial: A Comprehensive Guide](http://tylermcginnis.com/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)
is one of the better advanced tutorials that covers React concepts and code. It's a long slog, and it's in written in
JSX rather than ClojureScript, but it may help with understanding more of React's innards.