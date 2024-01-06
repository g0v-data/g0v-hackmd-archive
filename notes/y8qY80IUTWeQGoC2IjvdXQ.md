---
tags: FtO
---
# Facing the Ocean website

License: CC BY 4.0

## Volunteers

* isable
* chihao
* pm5
* hal

## Problems we need to solve

* "Is this still alive?"

## Information architecture

### What is the FtO?

- Why we do this
- What we do
- Event format
- History

### How to join

- Event schedule
- Telegram
- Hackmd book

### Projects

- Introduce some projects born in the past FtO events.
    - Her story
    - Is there any other collaborative projects?

### Who are we?

- Name and comments, photo of the organizers
- Some comments from participants

### Get in touch

- Telegram
- Mailing list
- Slack?

### Past events

- Link and beautiful/fun photos

## Sytem architecture

Hal recomments to use GatsbyJS or Hugo as a static page generator.
In short: If FtO site is enough simple, Hugo is easy for everyone, if we have React developers, and we will need customization, Gatsby is clean and modern way.

- [Hugo](https://gohugo.io/)
    - Pros
        - Easy, lightweight
        - Small learning curve
        - There are many [templates](https://themes.gohugo.io/)
    - Cons
        - Deep customization is bit difficult
        - Not Support typescript
    - Notes
        - Hal has built [this site](https://stamping.code4japan.org/) using Hugo

- [GatsbyJS](https://www.gatsbyjs.com/)
    - Pros
        - Support markdown page (plugin)
        - Based on React
        - Clean
        - If you know React, it's easy to customize
        - Support GraphQL
        - [Airtable plugin](https://www.gatsbyjs.com/plugins/gatsby-source-airtable/)
    - Cons
        - Big learning curve (Especially, if you don't know about React and GraphQL)
    - Notes
        - Hal has built [this website](https://mynumbercard.code4japan.org/) using Gatsby

> I haven't played with GatsbyJS before so this might be a good chance.  [name=pm5]
> I think ReactJS and GraphQL are worth learning. [name=sl]