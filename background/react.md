# React

This section covers the very basics of [React](https://facebook.github.io/react/index.html), with emphasis on the
parts of the library that are relevant to Untangled web development.

## Virtual DOM

Modern browsers are really, really fast at processing Javascript. It turns out that rendering the DOM is much more
expensive.

This presents a problem for Javascript web apps that handle a large amount of state. When the state changes, and
Javascript has to make 15 changes in 10 different places in the DOM, the changes occur quickly but the re-render
takes appreciably longer (TODO: source?).

React solves this problem with Virtual DOM...

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