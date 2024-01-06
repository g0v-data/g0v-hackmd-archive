# 1015 Hackthon Discussion 

Sign up:
1. mashbean
2. jacky
3. HC




### Goal

Define the priorities and roadblocks for implementing XPOC framework in Taiwan 

**Proof of Loop**

Content Creator Web - Content - Audience - Check -> Creator's Web

### Problem

- What are we solving?
    - There’s no good way to verify content from various platform all came from the authentic original source
        - All verification methods are platform specific
        - All verification provider is centralized
- What is the pain point?
    - Pain point is not pressing or urgent, until a bad scenario happens (user gets impersonated..etc)
- What is the user story?
    - I am a news media about to start reporting on the presidential election. I want to make sure no one impersonates my accounts on any platforms and share false or inaccurate information
    - I want to have a place where all my most important links to my content is organized and stored
    - I am a audience of [READr](https://www.readr.tw/), and I came across a YouTube video recommended to me by READr. However, the account had relatively few followers, and I wasn't sure if it was an official account. So, I opened the XPOC extension, and it displayed the XPOC verification badge next to the video. I clicked on the badge, which guided me to the official READr website. On that page, I found links to READr's YouTube, Facebook Page, Twitter, and other platforms. This gave me confidence that the video indeed came from the genuine READr organization.

### Memo should include:
People with technical knowledge might perceive the cost as very low, but the current task is to convince the media management level to endorse this, so that the entire group can be involved.

the proposal for the media group owener
(e.g.天下(TWG Media Group)'s opinion, the Reporter)
and executed by the developer (The cost is extremely low)

1. Purpose
2. Method
3. Pros/Cons
4. Endorsement from Legal Team

self-media user is not the priority.


### Other relevant solutions/products/technology

- Link Tree / [bento.me](http://bento.me) / portaly
    - Centralized platforms where all trusted links of a user is organized
- https://link3.to/
    - Web3 decentralized platform where trusted links of a user/wallet address is organized
    - (eg. https://link3.to/taipeicity)
- RSS
    - Newly updated content is pushed out to various subscribers who cares about my content
- Blue checks
    - Instagram/Twitter/YouTube all have platform specific blue checks

### Known Technical Issues

- No centralized server with manifest mapping makes it difficult to create smooth user experience that encourages adoption
- XPOC is only able to verify accounts, not able to infer content verification under a verified account
- Assumes user website content has not been hacked or maliciously altered.

### Known Product Concerns

- Assume users has resources to host its own website.
    - Independent content creators without a website has nowhere to host the manifest
- Product name/branding is ineffective and unmemorable
- Lack incentive to implement without a crisis - is there a way to make it sexy?

### Scope

- Assume origin website is trusted, no need to verify original website belongs to a certain person (though web3 wallet solves like like [link3.to](http://link3.to))
- Assume end user has their own website resources, since our current target audience is news media which all have their own website

### Problem to solve

- How do we convince traditional media in Taiwan to implement XPOC on their website?
    - What happens if you don’t implement it?
    - What are the benefits to implement it?
    - How much resources does it take to implement it?
- What is the MVP? How do you describe it
    - A decentralized LinkTree that works in reverse. Go from the content/account back to the trusted source

### Potential Solution

A. Locally stored subscribed manifest 

- Browser extension that stores manifest of sources I trust and care about locally
- Local content/webpage is able to show an XPOC (verified sign) on the frontend
    - similar to a blue check, that hyperlinks to the original source (website)

B. Centralized server 

- A trusted and politically insensitive organization or authority to store the mapping of manifest to enable quick look up and checking of content across the web
- (compared to the last solution, solves the need to subscribe actively)

### Conclusion

- Solution A makes the most sense from a technical and product perspective
- Onboarding traditional media to use XPOC requires a more convincing and cohesive narrative.
- XPOC needs a rebrand, name/logo/one liner that describes exactly what is.


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3fa5e629fd45aff8ee572237a2325caf.png)


**Question that collected:**
1. How can users on the social platform confirm that this is an official account?
2. The name "XPOC" is difficult to realize; "decentralized blue check" sounds cooler.
3. We need the product feel sexy, attractive webpage, Twitter bio, FrontEnd designer.
5. When verifying, it's not feasible to check every post. Does the content need manual updates from the web owner side? e.g. Automatically add content to the menifest (several videos list added by the TV media every day).
6. It's a bit impractical for Content Verifiers to enter XPOC URIs. Can there be a centralized place for mapping to make tracking easier? (Centralization vs. decentralization issue). Who is the best host? Put it on github.io? Self-submit, then confirm text string is the domain name owner through DNS?
7. User: Fact Check Group vs. End User - Extension is better or the viewer is better?
8. Centralized vs. Decentralized
    1. RSS Manifest hosted by the weblink owner
    2. Centralized Mapping
    3. Reversed Linktree?

Action Item:
1. Con-call 
2. Revised Document
3. Focus Group 