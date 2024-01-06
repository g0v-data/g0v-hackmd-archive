---
tags: cofacts
---

Cofacts Design Decision
===
## Basic principle
The whole design decision making and development direction of Cofacts are based on our core value and fundamental spirit when starting this project. This principle helps us when facing dilemmas or decision making, we are able to choose whatever is the closest to our concept.
Like when there’s no data indicating which is better, when there’s no similar product we can learn from, when facing a deadlock etc. Our fundamental value helps us cut out other options like a razor.

Also it’s because Cofacts has the following feature:

- Transparency: The whole process of developing and decision making of Cofacts is open to public to view and examine, we hope our whole community can take part in discussions.
- Community: In the process of hoax-busting, different users take their part in it. They are not just someone who respond to your request, they may be people from different field of expertise or people with different opinion, etc. People with different perspectives are involved in it.
- New Ideas: Users won’t be using Cofacts as originally intended, the community may develop a brand new way of using Cofacts the more they use it.
- Non-profit: The design of Cofacts is not about pursuing fame, wealth, or website traffic. Our core value is to achieve civic nationalism by interacting with our users.

Therefore, we develop and adjust Cofacts progressively by spreading our core value out.

### Spread the spirit of media literacy: promoting society’s awareness of media influence, teaching them to have a critical eye toward media and to learn how to interpret information and evaluate more efficiently.

To solve the fundamental problem of misinformation is to start from educating society about media literacy, about how to interpret information sent from one-way communication and evaluate it more efficiently. This can also prevent the spread of misinformation.

It’s hard to stop misinformation from the source and there’s a risk of becoming a violation of freedom of speech if we ban them on the internet or service platforms.

Therefore, we collect and organize every text sent into our system, we invite everyone to be a part of the verification and to examine the credibility behind each information. By exposing and refuting misinformation, we’re able to remind users of the possibility of unreal messages and to always be cautious and be doubtful before trusting any message received. Knowing there is more behind the cover and always emphasize the importance of fact-checking.

Besides some short description, we also encourage editors to attach related articles or news so we can cultivate a broad reading habit for society, having society see this world not just from biased hearsay from friends or family.

Just like historical facts v.s. historical interpretation, one single historical fact may have different interpretations due to different perspectives.

We hope to educate friends who used to only take in information from hearsay to realize that some of the messages might not be true. They may be unscientifically tested and taken completely out of context. Or even worse, they may be just biased thoughts from the writer.


### Promote dialogues with those who have different opinions in the community, especially to acknowledge that there’s no definite answer to one question.

What’s spreading among communities is not just hoaxes or rumors but also biased personal opinions. Whenever there’s a significant agenda, such as Cross-Strait Agreement on Trade in Services, same-sex marriage etc. Most opinions will be shown on wherever makes the writer feel belonged or comfortable like one’s Facebook page, blog, etc. Along with the rising of the awareness, the demand of linking original post and commenting are also rising. Cofacts as a place of providing a service to link suspicious messages and responses in order to lower the barrier to entry, promote citizens’ debate, which should mean a lot to society.

On the other hand, the reason why those kinds of message can raise awareness is also because there’s no “correct” answer to the question. Any side of the argument is not based on a known fact but one-sided opinions against its opposite side. This is a field that the traditional “fact-checking” system won’t have. However as a service of linking and commenting, it doesn’t have the obligation to avoid personal opinions.

### Be Able To Fallback
During the process of our design decision making, whenever we are not sure about which direction of development we want to go, we tend to keep the most versatile option for future possibilities. Which means the solutions we take are most likely to be undone or pivot into another.

### Experimental Propensity in the Community
Our belief is through massive discussion and verification, we can be closer and closer to the fact, even with minor questionable verification processes of results. Eventually, by evening out the odds we can make the final result more credible or acceptable. Therefore, we make the verifying process to be a collection of data rather than to be restricted to a single voice.

## Categories of Response

What can be used to categorize your response to a request?

Apply the Concept of **Be Able to Fallback**

- Contains true information.
- Contains misinformation.
- Contains personal perspective
- Invalid request
    - A question.
    - Fragmented or clipped message.
    - Message being too short.

---

#### Catagory 1: Outdated

**Outdated** is a category for events or messages which are within a certain time limit. With the old categorization system, it will fall into two kinds of category, “contains true information” and “contains false information” to describe its true content but outdated time limit.
- https://cofacts.g0v.tw/article/AVthoaMItKp96s659D8g
- https://cofacts.g0v.tw/article/5410472256241-rumor
- https://cofacts.g0v.tw/article/AVt1DD93tKp96s659EE1

#### Outdated - design decision making
![Outdated](https://i.imgur.com/PZImKEr.jpg)

1. **Method 1:Add a new category “Outdated”.**
The photo above shows how a message is considered outdated. There are two possible scenarios: It’s already outdated when requested or estimated to be outdated in the future. For messages which are estimated to be outdated in the future, the category “Outdated” can’t fit in the situation effectively. Try to imagine a request post which had been categorized as “true information” during its effectiveness, by the time it passed its due time there will be plenty of “true information” tags on it. The situation can be misleading to the editors to ignore that the post required to be updated as “outdated”. The “true information” category then will be a barrier to acknowledging its falsity.


2. **Method: “True But…” a category for situational usage.**
To avoid the issue described above in [1.] we came up with a new situational category to set its condition to be “true” in a specific situation. The users may judge if it’s still valid from its situational limit. For instance, the situational limit can be: `before 2017/06/30`, `before raising $100,000`, etc.


3. **Method: Set an expiration time for the responses.**
Create an option for editors to set an expiration time for the response before submitting. After the response is expired, the request post will be marked as “unresolved” again for new responses but former responses will be archived as reference. Therefore, the request posts with outdated response can be put back into the list of unresolved again.


Designed in consideration of:
- Categories which can be understood easily by LINE users.
- Educate users about the possible situation of request posts going expired so that users can take these kinds of situational request post more seriously.


We feel there’s a need to make “Outdated” stand out from “Contains misinformation”. At the same time, we should import the function to set expiration time to handle the issue of resolved request posts going outdated.


#### Catagory 2: Unproven

“Unproven” is a category for hypotheses or information that cannot reach agreement but cannot be categorized as “False information”. This is because it may contain information that is partly true, but it is still in discussion or in the experimental validation process.
Example:
A new untested and unproven way to perform CPR
https://cofacts.g0v.tw/article/AVrGYUx3yrDaTqlmmqTr

#### “Unproven” - design decision making
It can happen rarely and at the same time “Unproven” can fall into the category of hypotheses or information that cannot reach agreement so we combine it into “Opinionated”.

---
#### Opinionated

“Opinionated” is about personal opinions and as a service of fact-checking itself, Cofacts should have ignored this kind of requests. Although based on user MrOrz’s theory, it’s ideal to promote an exchange of perspectives and opinions through the process of verification in order to achieve civic literacy.

Examples:
- Hypothetical question: https://cofacts.g0v.tw/article/5484897542512-rumor
- Personal opinion: https://cofacts.g0v.tw/article/5715856402861-rumor
- Conspiracy theory: https://cofacts.g0v.tw/article/5549374955095-rumor

#### Opinionated - design decision making

1. **Method 1: Remove “Opinionated”**: It can be considered as an “invalid request” but the wording for “fragmented or clipped message” have to be changed.
The tag “invalid request” is most likely about format errors and not about the content itself. It is unsuitable to combine them.

2. **Method 2: Use “Opinionated” as a category to discuss about personal opinions**
Summarize “other personal opinion” and list the resource link. It’s acceptable if the reference is another personal opinion.
Since it’s a personal opinion, it cannot be verified objectively. Instead of leaving it unresolved, making it an opportunity to start dialogues with those who have different opinions seems like a better option.
The problem probably is that it’s hard to find a third-party of the opposite side when it comes to personal opinion, which leads them into a state that nobody wants to respond.

Considering to fit into two design principles:
1. `Be Able To Fallback`, we should give the flixibilty by using mapping or remove the reference directly.
2. `Promote dialogues with those who have different opinions in the community`
We decide apply Method 2.

