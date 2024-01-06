# Cofacts Website --> nextjs 12up

## Data fetching

NextJS supports ISR for pages.

As server-rendered props are passed to UI using JSON managed by next.js, it does not make sense to dehydrate & rehydrate the entire Apollo cache from server-render logic to client.

### Landing page

- Statically rendered for whole page
- client-side render for list of articles, numbers, etc

### Tutorial page, about page, etc

- Same; all client-side requests.

### Article detail page

- `getStaticPaths`:
    - `fallback: true`; component should render skeleton
- `getStaticProps`:
    - Props
        - Article text
        - similar article
        - article replies
        - hyperlink to article replies
    - Problem: How do we revalidate using [on-demand revalidation](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration#using-on-demand-revalidation) when
        - feedback is added (changes order of article replies)
        - reply is added
        - new article is added (may invalidate similar article's similar article list!)
- client-rendered:
    - numbers
    - Logged in components such as voting, editor, etc
    - comment text
    - analytics
    - hyperlinks (rumor hyperlinks are not worth server-rendering)

Use [`getStaticProps`]()

## Others
- Typescript support
- Apollo-client v3 (client-side requests only)