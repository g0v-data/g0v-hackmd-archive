---
tags: cofacts
GA: UA-98468513-3
---

# Cofacts preview generation

- Rumors-site: OG image for articles & replies
  - note: can be done in https://nextjs.org/blog/next-13-3
- Rumors-line-bot: OG image for LIFF
    - For sharing
    - For third party line bot to use in its carousel
- Can also consider create a new, dedicated repository for this
- 2023/2/11 認領： Alvin

## Dev info

- [Vercel/Satori](https://github.com/vercel/satori)
    - https://vercel.com/docs/concepts/functions/edge-functions/og-image-generation
- A HTTP endpoint; can deploy as a separate cloud function
- If site and LINE bot shares OG image, can develop standalone repository
    - But if site and chatbot has their own style, we can consider develop inside its retrospective repo
- Consider caching

## Content to show

Ref
https://www.figma.com/file/1ptgfJbrhoRWenQ1RPNyb9/Post-image?node-id=3%3A211

- Article text
- Image / Video thumbnail in background
- Statistics
    - Reply request count
    - View count
    - Summary of replies

