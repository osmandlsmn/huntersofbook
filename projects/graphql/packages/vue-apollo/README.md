![alt text](https://github.com/huntersofbook/huntersofbook/blob/main/docs/public/images/graphql-vue.png?raw=true)


# Vue 3 Apollo

<p>
      <a href="https://www.npmjs.com/package/@huntersofbook/vue-apollo"><img src="https://img.shields.io/npm/v/@huntersofbook/vue-apollo.svg?style=flat&colorA=002438&colorB=28CF8D" alt="Version"></a>
      <a href="https://www.npmjs.com/package/@huntersofbook/vue-apollo"><img src="https://img.shields.io/npm/dm/@huntersofbook/vue-apollo.svg?style=flat&colorA=002438&colorB=28CF8D" alt="Downloads"></a>
      <a href="./LICENSE"><img src="https://img.shields.io/github/license/huntersofbook/huntersofbook.svg?style=flat&colorA=002438&colorB=28CF8D" alt="License"></a>
</p>


## Description
Graphql Vue 3 Apollo
- Vue 3 Support
- Only ESM Support
- Apollo Client 3 Support

## Installation

```bash
pnpm add @huntersofbook/vue-apollo
```


## Demo 

### Vue 3 with Vite Demo

[![Edit @huntersofbook/vue-apollo](https://codesandbox.io/static/img/play-codesandbox.svg)](https://githubbox.com/huntersofbook/huntersofbook/tree/main/projects/graphql/playground)

Code for the demo is in [playground](../../playground) folder.

### Nuxt 3 Demo
[![Edit @huntersofbook/vue-apollo](https://codesandbox.io/static/img/play-codesandbox.svg)](https://githubbox.com/huntersofbook/huntersofbook/tree/main/projects/graphql/playground-nuxt)

Code for the demo is in [playground-nuxt](../../playground-nuxt) folder.

## Usage

```ts
import { DefaultApolloClient } from '@huntersofbook/vue-apollo'
import { ApolloClient, InMemoryCache, createHttpLink } from '@apollo/client/core'

// HTTP connection to the API
const httpLink = createHttpLink({
  // You should use an absolute URL here
  uri: 'https://countries.trevorblades.com',
})

// Cache implementation
const cache = new InMemoryCache()

// Create the apollo client
const apolloClient = new ApolloClient({
  link: httpLink,
  cache,
})

provide(DefaultApolloClient, apolloClient)

```

## Codegen

```bash
pnpm add -D @graphql-codegen/add @graphql-codegen/cli @graphql-codegen/typescript @graphql-codegen/named-operations-object @graphql-codegen/typescript-apollo-client-helpers @graphql-codegen/typescript-operations @graphql-codegen/typescript-vue-apollo
```


codegen.yml
```yml
overwrite: true

documents: ./src/graphql/**/*.graphql

schema: ./schema.graphql
emitLegacyCommonJSImports: false

generates:
  ./src/graphql/types.ts:
    plugins:
      - add: {content: '// THIS FILE IS GENERATED, DO NOT EDIT!'}
      - add: {content: '/* eslint-disable eslint-comments/no-unlimited-disable */'}
      - add: {content: '/* tslint:disable */'}
      - add: {content: '/* eslint-disable */'}
      - add: {content: // @ts-nocheck}
      - typescript
      - typescript-operations
      - typescript-apollo-client-helpers
      - typescript-vue-apollo
      - named-operations-object
    config:
      enumsAsTypes: true
      withCompositionFunctions: true
      vueApolloComposableImportFrom: '@huntersofbook/vue-apollo'
      vueCompositionApiImportFrom: vue
```

```bash
pnpm graphql-codegen-esm --config codegen.yml
```



## 💻 Development

- Clone this repository
- Enable [Corepack](https://github.com/nodejs/corepack) using `corepack enable` (use `npm i -g corepack` for Node.js < 16.10)
- Install dependencies using `pnpm install`
- Stub module with `pnpm dev:prepare`
- Run `pnpm dev` to start [playground](./playground) in development mode



## Inspiration
Codes in this build are inspired by [Vue](https://github.com/vuejs/apollo) and from there the codes were copied. Thanks you for your great work.
Thank you [Akryum](https://github.com/Akryum)
Thank you SSR code [fabis94](https://github.com/fabis94) and [PR](https://github.com/vuejs/apollo/pull/1436)

 ## License

MIT License © 2023-PRESENT [productdevbook](https://github.com/productdevbook)

