# Typescript adoption

We would like to introduce Typescript to Cofacts code repositories, so that the data flow from API to UI can be documented.

This would help a lot when we revamp in the future, enabling us to move fast but still not breaking things.

## Strategy
Aim for interfaces first
- Typing data source with [GraphQL codegen](https://the-guild.dev/graphql/codegen)
- Typing render function by [declaring and colocating fragments](https://the-guild.dev/graphql/codegen/plugins/presets/preset-client#embrace-fragment-masking-principles)

## rumors-site
- Introduce GraphQL and GraphQL codegen codegen w/ client preset
    - completed in https://github.com/cofacts/rumors-site/pull/500
- Type article detail, article list pages' requests and page components
    - Focus on pages that have intensive data requirements
- Type `lib/` and `components/` that will be reused after revamp
    - Remove string fragments

### Avoid typing these
- CSS-in-JS related stuff - We want to move away from CSS-in-JS due to its runtime overhead, and too much effort to consistent SSR with CSS-in-JS.

## rumors-line-bot
- Introduce GraphQL and GraphQL codegen w/ client preset
- Typing individual handlers
- Typing utility functions
    - Use type definition from offical LINE messaging API package
- Typing webhook handler
- Typing GraphQL resolver

### Avoid typing these
- Svelte related UI
    - Probably replace with React in the future, don't have the luxury supporting two different frameworks

## rumors-api
- Add non-null to fields whenever possible
    - So that clients don't need to handle `null` cases that cannot happen
- Typing resolvers and helpers using [typescript-resolvers](https://the-guild.dev/graphql/codegen/plugins/typescript/typescript-resolvers) plugin


