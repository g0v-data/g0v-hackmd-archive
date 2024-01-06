# Cofacts website with Next.JS & React 18 server components

###### tags: cofacts design-doc

## Article page
- `getStaticPaths`: Generate top articles w/ blocking fallbacks
- `getStaticProps`: article text, article replies?
    - Note: props loaded here does not populate apollo cache
- React client component: Feedback, Reply editor, edit buttons
    - can use useQuery / useMutation
    - update article replies: ? does that reflect aritcle replies in `getStaticProps`?
- React server component: ?

## References
- React server components https://nextjs.org/docs/advanced-features/react-18#react-server-components
- Incremental Static generation https://vercel.com/docs/concepts/next.js/incremental-static-regeneration