---
slug: "/node-sdk"
title: "Node.js"
---

# Node.js SDK

Empower your Node.js scripts to upload screenshots with the Argos SDK, or craft your own using `@argos-ci/core` for seamless interaction with Argos.

The SDK is available as an [npm package](https://www.npmjs.com/package/@argos-ci/core) and the source code is open sourced on [GitHub](https://github.com/argos-ci/argos-javascript/tree/main/packages/core).

## Installation

```sh
npm install --save-dev @argos-ci/core
```

## Usage

To upload screenshots from a `./screenshots` directory, you can use the `upload` function provided by the SDK:

```js

await upload( root: "./screenshots" );
```

## API Reference

For a detailed breakdown of the available SDK functions and their use, please refer to the [SDK reference documentation](https://js-sdk-reference.argos-ci.com).
