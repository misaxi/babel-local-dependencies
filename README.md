## Problem
- You follow good principle of system design to build small modules and let them talk to each other.
- You write JavsScript in ES6 standard and use [Babel] to transpile.
- And you use [npm local dependencies] to wire them up.
  ```json
  {
    "dependencies": {
      "auth-module": "file:auth-module",
      "domain-module": "file:domain-module",
    }
  }
  ```
- Then you find out that [Babel ignores files in the node_modules] by default.

## Solution
- Write your own `ignore`/`only` logic
- Or, use this module

## How to use this module

```
$ npm install babel-local-dependencies --save
```

```js
require('babel/register')({
  only: require('babel-local-dependencies')
})
```
## How does this module work
- Look through your `package.json` for local dependencies
- It transpiles all the supported files of the local dependencies
- It does not transpile files under node_modules of the local dependencies

[npm local dependencies]: https://docs.npmjs.com/files/package.json#local-paths
[Babel]: https://babeljs.io/
[Babel ignores files in the node_modules]: https://babeljs.io/docs/usage/require/#usage
