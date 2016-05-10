# Introduction to Untangled
A high level overview of the emerging Clojure(Script) web development framework based on React and Om Next.

> NOTE: This introduction is in active development -- the content may not be completely accurate.
Please feel free to submit PRs!

## Rationale

I joined the Untangled team as part of my first programming job out of college. The extent of my web development
experience was static HTML and CSS with some very basic Javascript and jQuery.

When we began developing Untangled on top of Om Next, we discovered that the combination of Om, React, and ClojureScript
was a lot to swallow all at once. Untangled has significantly helped with streamlining the development process with
these three technologies.

However, despite its elegance, Untangled development is far from trivial for those who are unfamiliar with the
technologies. This is partially by design -- we want to take advantage of the best each technology has to offer, which
demands a certain depth of knowledge. The part not by design is the reason the framework is alpha!

Tony Kay's [Untangled Tutorial](https://github.com/untangled-web/untangled-tutorial) is an excellent place
to start for those developers who enjoy jumping into the deep end and figuring out how to swim. For those of you
(like me) who prefer to take swim lessons in the shallow end first, this introduction is for you.

__This project has two primary goals:__

1. Follow in the footsteps of [Randall Munroe's Thing Explainer](http://xkcd.com/thing-explainer/) by describing
Untangled's design using the least possible technical jargon without sacrificing technical accuracy.

2. Prepare those with programming experience, but minimal backgrounds with Untangled's component technologies, to get
started with Untangled and quickly plow their way across the pool to the deep end.

## Assumptions

> a.k.a: what is far outside the scope of this tutorial and I couldn't possibly explain better than existing materials.

- You are familiar with [Clojure(Script) syntax](http://www.braveclojure.com/introduction/). You know what a macro is.
- You know how to build a simple ClojureScript application. [Modern ClojureScript](https://github.com/magomimmo/modern-cljs) is an excellent place to start.
Version 1 for [Leiningen](http://leiningen.org/), Version 2 for [Boot](https://github.com/boot-clj/boot).
- You have a basic understanding of web development (especially HTML and JavaScript). You have a general idea of what
the DOM is and you know how to modify it with standard Javascript (i.e. `document.body.innerHTML = "Hello, world!";`)
- You know something about functional programming, immutable data structures, pure functions / referential transparency,
 and [why someone might want to use functional programming over object-oriented models](https://medium.com/@jugoncalves/functional-programming-should-be-your-1-priority-for-2015-47dd4641d6b9#.edws4fjk3).

So, we assume you know a little bit more than Randall Munroe's ten hundred word limit, but we don't expect anything else.

__If functional programming is new and scary for you__... never fear, we will cover some of the reasons it is helpful
in Untangled as well.

## Table of Contents

1. Background (skip these sections if you already know about them)
    - [React](background/react.md) (what virtual dom is, the importance of the `key` attribute, and lifecycle methods)
    - Om Next (UI tree vs. data tree, one source of truth for app data, syncing state change and UI updates)
        - I am NOT interested in exploring the internals of Om or the reconciler. Theoretically, you do not need
        to know how these work to use Untangled.
    - Model / View / Controller paradigm

2. Untangled Client Enlightenment
    - Model: App-state database and `idents`
    - View: `defui`, components, and the UI render lifecycle.
    - Controller: queries, normalization and denormalization, mutations
        - It is especially important to emphasize that how you get data _out_ is not the same as how you put data _in_.

3. Untangled Server Enlightenment
    - Coming soon

4. Untangled Datomic Enlightenment
    - Coming soon
