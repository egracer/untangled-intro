# React

This section covers the basics of [React](https://facebook.github.io/react/index.html). React operates as the
view in Untangled's MVC architecture, so understanding it's behavior will help tremendously when building your web app's
UI.

## Virtual DOM

#### Overview

Firstly, [CSS Tricks](https://css-tricks.com/dom/) has an excellent, brief primer on the DOM if you need a refresher.

It turns out that rendering the DOM is expensive, because [it was not originally designed for the complex web
apps that we use today](http://tonyfreed.com/blog/what_is_virtual_dom). Thus, large web-apps that frequently modify the
DOM can quickly become sluggish performance-wise.

React was built to minimize DOM modifications, so that the render process is as efficient as possible. Even though
rendering the DOM is an expensive operation, browsers have become exceptionally efficient at interpreting Javascript.
React's virtual DOM is a lightweight copy of the DOM stored within Javascript. When you make changes to the virtual DOM,
React executes a diff algorithm to determine exactly what changes have occurred. Then it batches the virtual DOM changes
and applies them to the real DOM, which the browser proceeds to render.

In other words, React minimizes DOM modifications by doing what computer scientists do best – adding another layer of
abstraction. Standard Javascript directly modifies the DOM. React, by contrast, does not want you to modify the DOM.
You modify the virtual DOM instead, and React reconciles the virtual DOM changes into a highly optimized DOM modification.
We will cover a bit more about the reconciliation process below.

So, by keeping track of desired changes to the DOM within Javascript, and batch applying the fewest changes necessary to
reflect the web app's changing state, the browser renders fewer changes to the DOM and does so less frequently than
repeated calls to the slower DOM manipulation functions.

There are [plenty of resources listed below](#more) that discuss virtual DOM in more depth.

#### React Elements

React Elements are the building blocks for the virtual DOM. There are two kinds of Elements, DOM Elements and
Component Elements. A DOM Element is a collection of data needed to create a virtual representation of a standard DOM
tag (div, p, table, etc.). A Component Element is a grouping of DOM Elements and other Components that render
the data passed into it through `props`.

Untangled requires that all DOM Elements are rendered within Component Elements. We will cover how to create React
DOM Elements and Components in the [View]() chapter of the introduction. Before we get our hands dirty with building a
working UI, it is important to understand the `props` and `key` properties of React Components, and how they affect
rendering behavior.

## Props and Component Local State

Both are just maps of data that a Component uses to determine what will be rendered in the DOM. When either a component's
props or its state is changed, React initiates the virtual DOM to real DOM reconciliation process.

The key difference between the two is that `props` are derived from global app state, while component local state only
exists within the component's virtual DOM instance. Once the component is unmounted from the screen, its component state
is destroyed.

If the UI triggers an action that should persist data even if the component is unmounted, make sure that said data is
saved to the global app-state so that it reappears in `props`. Only use component state for transient data.

If you want a slightly more thorough breakdown of props vs state, [the HootSuite developers have a great explainer](https://github.com/uberVU/react-guide/blob/master/props-vs-state.md).

## The `key` property

How, exactly, does React 'reconcile' the virtual DOM into real DOM?

As mentioned, the process is initiated when there is a change in a component's props or local state. React compares the
old props and the new props, and if they aren't equal, then the component is marked as requiring a re-render.

One way that React minimizes DOM manipulation is by using the `key` property, which helps it to keep track of the
unique pieces of the DOM as the application state evolves over time.

For the purposes of Untangled, any time that you iteratively generate a list of DOM Elements or Component Elements, you
need to provide a key property that is _unique to that level of the DOM tree_. We will cover how to do this in the
[View]() chapter of the introduction. If you iteratively generate elements that do not provide key properties, you will
see this error:

> react.inc.js:18780 Warning: Each child in an array or iterator should have a unique "key" prop. Check the render method
of `ComponentName`. See https://fb.me/react-warning-keys for more information.

So, now you know what that means! To fix it, you need to find the list of React Elements lacking key properties in the
component specified by the error message.

The [The React documentation on multiple components](https://facebook.github.io/react/docs/multiple-components.html#children)
describes more about how the key attribute is used. It also describes more about the reconciliation process.

## DOM Reconciliation and the Render Lifecycle

You can override the default implementations of React lifecycle methods in your components. For more information on how
these functions are best used, see the [React docs on Lifecycle Methods](https://facebook.github.io/react/docs/component-specs.html#lifecycle-methods).
We will cover how and where to add these methods in the [View]() chapter.

1. When a component has been initialized and is about to be reconciled to DOM, `componentWillMount` is triggered. Changes
to component local state in this function will be rendered as if they had been made before the component was mounted.
2. Once the component has been reconciled to DOM, all of its child components will be mounted (calling `componentWillMount`
and `componentDidMount` on each) before its `componentDidMount` is triggered.
3. When a component receives new props and is triggered for DOM reconciliation, `componentWillReceiveProps` is triggered,
with the new props as an argument.
4. When a component receives new props OR new state, `shouldComponentUpdate` will be triggered. It should return a
boolean value. If true, the component will undergo DOM reconciliation. If false, it will not.
5. `componentWillUpdate` and `componentDidUpdate` are triggered respectively before and after the component is reconciled
to the DOM. The first function has the new props and state as arguments, the second has the old props and state as
arguments.
6. When a component is going to be removed from the DOM, `componentWillUnmount` is triggered.

## <a name="more"></a>Additional Material

For those who are interested in learning more about React, I recommend looking at:

- [Thinking in React](https://facebook.github.io/react/docs/thinking-in-react.html), an excellent and concise primer on
how React UIs are intended to be designed.
- [React (Virtual) DOM Terminology](https://facebook.github.io/react/docs/glossary.html)
- [React.js Tutorial: A Comprehensive Guide](http://tylermcginnis.com/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)
is one of the better advanced tutorials that covers React concepts and code. It's a long slog, and it's in written in
JSX rather than ClojureScript, but it may help with understanding more of React's innards.