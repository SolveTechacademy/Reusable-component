# CSS via Components

A single React component to inject CSS with ease.<br>
It works with SSR (even using React 16's [renderToNodeStream](https://reactjs.org/docs/react-dom-server.html#rendertonodestream)) and client-side rendering out-of-the-box.<br>
It also provides an *optional* optimisation path.

## Installation
```sh
# yarn
yarn add react-css-component

# npm
npm i --save react-css-component
```
> **Caution**: It requires `react` and `prop-types` to be present.

## Why?
This package was created as a possible solution to a [question](https://twitter.com/solvetech_a) by [Nkam Valery](https://twitter.com/solvetech_a).<br>
Creating resuable React components in general is pretty easy, but adding styling is not. The simplest way is to just use [inline style](https://reactjs.org/docs/dom-elements.html#style), which works pretty well for many basic components. Yet, it is very limited. Neither do we have have pseudo classes nor do we have media queries.<br>
So, at some point, we need actual CSS. We could include a CSS file, but that would require an additional build step e.g. using [Webpack](https://webpack.js.org) in combination with its [css-loader](https://github.com/webpack-contrib/css-loader). While this would work, it's not very compelling to enforce a certain build tool, just to use a single component.<br>
Alright, how about [CSS in JS](http://michelebertoli.github.io/css-in-js/)? Using plain JavaScript to style the component sounds great, as the component is written in JavaScript anyways. But, [most CSS in JS solutions are way to big to depend on](https://github.com/hellofresh/css-in-js-perf-tests#bundle-sizes). They're built for applications, not for independent reusable components. Yet, we can still benefit from writing our CSS in JavaScript. This package is the attempt to provide the smallest universal solution for inlining CSS in JavaScript possible.

## How?
Depending on whether [universal rendering](#universalrendering) (server-side rendering with client-side rehydration) or [client-side only rendering](#clientrendering) is used, the implementation uses a different logic.

