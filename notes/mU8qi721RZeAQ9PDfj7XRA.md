---
tags: cofacts, chatgpt
---

# ChatGPT or LLM to aid fact-checking

Large language models can be helpful to human beings when they encounter internet hoax.

:::info
- Assistive fact-checking is part of [Community Layer in CCPRIP](https://g0v.hackmd.io/@cofacts/rd/https%3A%2F%2Fg0v.hackmd.io%2FBRsJOevWSbyUMBSZEVVWrA).
- Engineering design doc for implementation: https://g0v.hackmd.io/@cofacts/rd/%2F%40cofacts%2FrknFrmdk3
:::

## Use cases and usage

:::spoiler Previous brain storm result: Scenario #1~#7

### Scenario #1: point out suspicious points for messages not debunked yet

[Fatima by Aos Fatos](https://www.aosfatos.org/noticias/aos-fatos-e-facebook-unem-se-para-desenvolver-robo-checadora/) is a bot that helps its user to perform basic media literacy actions, such as separating news from opinions, during the conversation.

With the power of ChatGPT, it is now possible for Cofacts chatbot to demonstrate these steps of breaking down messages for further investigation, which may be helpful when a message has not been replied by fact checkers yet.

#### Extended goal: Provide users with keywords to google 
(Future work)

After analyzing the suspicious points, the next step to fact-checking should start with browsing the web.

[ChatGPT browsing plugin](https://openai.com/blog/chatgpt-plugins#browsing) shows that ChatGPT is able to
1. Generate what to search
2. Pick from search results
3. Summarize from the search result

According to OpenAI's [WebGPT blog post](https://openai.com/research/webgpt), they trained GPT-3 to first copy human demonstrations on using text-based browser to answer questions. Then reinforcement learning via a teacher model kicks in.

It should be valuable for Cofacts Chatbot users if we just take the first step -- generating Google keywords. This is a step to let Chatbot users learn how to Google -- This time, ChatGPT is the teacher.


### Scenario #2: Reply critique

> A.k.a 李姓中壢GPT

(Future work)

Aid fact-checkers with review and rewrites

- Role play -- see if AI is convinced
- Auto feedback?

### Scenario #3: Topic Categorization
(Future work)

- Put all categories in prompt
- Inference use case
  - Actually encoder-based model should work better than decoder based ChatGPT
  - Encoder based model: Good at understanding / decoder based model: Good at generation
- Few shot examples: retrieve similar articles and their categories.

### Scenario #4: claim extraction
(Future work)

- Extract fact-checkable claim
  - Can let users vote what do they care most
  - In the future, we can ask ChatGPT if a reply maps to the claims (scenario #2)
  - Claim - reply chunk mapping will be helpful in generating `ClaimReview`; we can also consider performing search on claim basis, so that long messages with multiple claims can be broken down and appear in other messages
- Extract opinions
  - Can let users reflect which sentence let them feel strong

### Scenario #5: Automatic reply with document QA

(Future work)
- Optional CoT step: claim extraction first, process facts and opinions differently
  - factual claims can be looked up on the Internet for groundness check
    - https://ai.googleblog.com/2022/01/lamda-towards-safe-grounded-and-high.html#:~:text=of%20the%20dialog.-,Factual%20Grounding,-While%20people%20are
    - https://arxiv.org/pdf/2201.08239.pdf
    - We can also index fact checker's fact check reports (in IR index and text embedding vectors) so tha-/t they are ready for retrieval
  - for opinions, look up text in similar category but different opinion in replies
    - We can also collect opinions and index them (in IR index and text embedding vectors)
    - Possible source: FB post of professional, 公視有話好說 transcript, 公視我們的島 transcript, 報導者文章 etc
- List related aritcles / replies
  - RAG techniques: https://www.promptingguide.ai/research/rag#modular-rag
  - Possible prompt design: role-playing -- user sending existing articles, assistant sending replies in the chat content history
- Optional CoT step: select relevant items from search result
- Generate response according to search result above

#### Extended goal

Collect documents / arguments from additional sources
- Other fact checkers
- Connect to https://toolbox.google.com/factcheck/explorer
- Opinion sources
    - transcript of 有話好說?
    - Facebook posts?

--> Other project

### Scenario #6: Automatic groundness checking with Auto-GPT
(Future work)


> How Auto-GPT works:
> - https://github.com/Significant-Gravitas/Auto-GPT
> - https://tracyting.com/agentgpt/ (GUI for auto-gpt)

Imagine an editorial room, with AutoGPT perform fact checking, and human acts as editors inspecting the result and provide directions. No content is published as a fact-checking reply until the human editor agrees.

This is the ultimate scenario -- An open and automated editorial room for fact-checking.

We can provide ChatGPT with the following information:
- Result from claim extraction (Scenario #4)
- Related article / replies (Scenario #5)
- Provide the following commands for LLM (AutoGPT style)
    - `conclude('conclusion', 'references in [1], [2], ...')`:
        - Call this if and only if collected information are sufficient to reflute or confirm the claims.
        - We will stop calling Auto GPT and mark the process as completed; highlighting the conclusion for human inspection.
    - `search('search term', 'reason')`:
        - Call this when AI wants to search for something.
        - Our program will perform search using search term, and return a list of SearchResult with ID.
        - The reason will be passed along with search result, so that chatbot can continue reasoning.
    - `visit(searchResult ID)`:
        - We will fetch the web content to chatgpt
- Can connect with reply critique in Scenario #2 to see if the reply is convincing enough. If not, provide reasons for not being convinced, and restart the process.
    - The reply critique bot can also be augumented with related document (Scenario #5 document Q&A) queried from opposite side -- Sort of like Generative Adversarial "Narratives" (GAN) that mimics real-world debates!

Human fact checkers can act as editors checking AutoGPT's response:
- AutoGPT's "fact-checking" process and ther critique on the results are public, hopefully these can ==inspire human fact checkers== and avoid directions that AutoGPT has proven not working.
- [Optional] Allow human fact checkers to give instruction to AutoGPT, provides new directions of investigation

:::

### AI assisted reply authoring
:::info
- 2024 initialtive
- Combines idea from Scenario #1 + #5, #6 + #2.
:::

When a new message comes in DB, we create a "conversation thread" that puts together:
- Surrounding information: cooccurred messages, previous reply to similar messages, search results, comments, etc
- User interaction: search again, provide comment, provide draft reply and ask for critique, etc

This conversation will be open to all logged in contributors, all contributors will see the same thread. This helps different contributors to work on the same conversation and co-create with AI's help.

#### UX on chatbot

When a new message comes in DB, provide an automated analysis with these messages in prompt
- In system prompt, instruct the AI to help user with media literacy and finding suspicous points
- Cofacts DB content as few-shot examples
  - If there are existing replies, compose examples with user posting hoax (along with cooccurred messages) and assistant posting existing reply.
  - If there are similar messages w/o replies, compose examples with user posting hoax (along with cooccrrred messages) and assistant reply with the create time, and state the fact that there are currently no replies yet.
    - This can be useful for fraud-related messages -- simply revealing someone else also submits this helps
- If image or video is used, perform image search on web using [Google vision ai web entity search](https://cloud.google.com/vision/docs/detecting-web) and provide result
  - May need a multimodal LLM to interprete these
- Search results from custom search engine (within an allowlist of IFCN fact checkers)
    - Or use [SearXNG](https://github.com/searxng/searxng) 

Then Cofacts chatbot can include the AI analysis in its reply if no human has created a reply.

> This is essentially scenario #1 with ideas in scenario #5. We don't need recursive techniques like [Re-Act](https://arxiv.org/abs/2210.03629), because we are able to attach all information we currently have in one prompt without the need to have any extra steps. We can of course ask AI to write reasons before any conclusions within its reply, though (chain of thought).

#### UX on website

When collaborators visit Cofacts detail page, they can activate the AI assistant sidebar; it will contain the information above, and AI's initial analysis.

The thread contains the past conversation from above, but with a different system message that ask the AI to help human writing replies with some inspiration. Point out the good and what needs to improve.

The user can interact in the thread with:
- Perform search (Cofacts + Custom search + web entity) again and see if there are more information
- Write comment -- Each collaborator 1 comment only, the same with 我想補充
  - When comment gets updated and it's the last human comment in thread, the last AI reply based on outdated comment will be replaced with new AI reply based on the updated comment.
  - If there are others submitted comment, updating the old comment will appear as new speach bubble in the conversation, instead of in-place edit.

When composing reply, the user can:
- ask for critique (請 AI 幫看)
  - Generates a new thread that AI acts as the person sending hoax.
  - Same as scenario #2
  - The result summary will also be summarized in the original thread (public to everyone else), and generate further AI response based on that (Point out the good and what needs to improve.)
  - After critique, can ask AI to generate a rewritten reply
- Improve writing Confluence AI: https://youtu.be/kR4TKS3UlP4?t=121
  - Select and generate:
    - Improve fluency and fix typo / grammer errors
    - Shorten
    - Suggest title / topic sentence to the paragraph
  - Buttons on menu
    - Provide summary / topic sentence at front
    - Conclude at the end

## Related work

- 2018: automated fact-checking project Fatima by Aos Fatos https://www.aosfatos.org/noticias/aos-fatos-e-facebook-unem-se-para-desenvolver-robo-checadora/
- 2022/12 https://dcorney.com/thoughts/2022/12/09/inevitable-gpt3-post.html — 與 ChatGPT 的對話紀錄文。覺得可以用來作為 NLP pipeline 的一環，但事實精確度看起來並非 ChatGPT 訓練時最佳化的目標。
- 2023/04 https://psyarxiv.com/qnjkf — 直接拿來做 true/false claim classification，約有 72% accuracy 並聲稱可以幫助標記假訊息。
    - Evaluation dataset：politifact 上的 21,152 篇 statement + 5 種分類（true ~ pants on fire）
    - Prompt 就這樣：“Can you fact-check a claim for me? When fact-checking use clear language such as ‘true’ and ‘false’, and avoid negations”
- 2023/02 https://www.wired.co.uk/article/fact-checkers-ai-chatgpt-misinformation 2020 年起就有人用 BERT 做 ClaimHunter
- 【生成式AI】ChatGPT 可以自我反省! https://www.youtube.com/watch?v=m7dUFlX-yQI 提及的 paper：
  - DERA: Enhancing Large Language Model Completions with Dialog-Enabled Resolving Agents https://arxiv.org/abs/2303.17071
  - ReAct = Reason + Act https://arxiv.org/abs/2210.03629
  - Reflexion https://arxiv.org/abs/2303.11366
- 讓 AI 做計劃然後自己運行自己 https://www.youtube.com/watch?v=eQNADlR0jSs
  - Recursive Reprompting and Revision (Re3): https://arxiv.org/abs/2210.06774
- 2020/6/25 [Language Models as Fact Checkers?](https://ai.meta.com/research/publications/language-models-as-fact-checkers/)
- Exploring the ability of ChatGPT and Langchain to Fact Check Political Claims https://deepneuralnet.co.uk/
- fact checking with prompt chaining https://github.com/jagilley/fact-checker
- Langchain self-check https://python.langchain.com/docs/use_cases/self_check/
- Multi-agent framework MetaGPT https://docs.deepwisdom.ai/main/en/guide/get_started/quickstart.html
  - Can role play; define input / output and gets info from previous pool
  - browse web and summarize https://docs.deepwisdom.ai/main/en/guide/use_cases/agent/researcher.html
- 用 AI 評價文章的 paper，說不定可以拿來幫助查核協作者檢視自己的 reply 或是拿來檢視 AI reply
  https://arxiv.org/abs/2305.01937 / https://arxiv.org/abs/2310.05657
- 雨蒼對 Digital Peacebuilding Expo 的[投影片](https://docs.google.com/presentation/d/1g9af372EYbblCcyR3TzoFUERa-EMQrEOknr33PE2Nvc/edit)
  - [Depolarizing GPT](https://depolarizinggpt.org/) GPT 模擬左翼、右翼意見領袖回應，一次看兩邊
  - [Acquaint](https://www.acquaint.org/) -  提供對話情境，使用者要用比較好的說法回應
- [2024/4/29 - Reuters Institute - Generative AI is already helping fact-checkers. But it’s proving less useful in small languages and outside the West](https://reutersinstitute.politics.ox.ac.uk/news/generative-ai-already-helping-fact-checkers-its-proving-less-useful-small-languages-and)

## Usage & cost estimation

Assume:
- Each new article submitted to DB takes 1 ChatGPT request
- Each ChatGPT request takes 2.5K tokens (prompt + completion)
- We would be using `gpt-3.5-turbo`, whose cost is $0.002 / 1K tokens

In 2022, there are 25,000 newly created text messages.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2fac4e5206023863dc12c028abbb2c70.png)

We would spend `25000*1*2.5*0.002=125` USD per year (~10 USD per month) on creating automatic AI responses.

To further cut costs, we can also consider only generating AI replies to articles that have >=2 reply requests.

:::spoiler Token count estimation
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_24869c95ba0be91913f95157d31b3eff.png)

Total request = 8
Total tokens = 17,243
Around 2.5K tokens per request
:::

## Prompt design

We record our experiments on ChatGPT prompts here:
https://docs.google.com/spreadsheets/d/e/2PACX-1vQSOFMGdiiHSXzh7j3ZpKnMRtSNDhKip1xrtxxW3wiF2CbISz3tipNw6Uw2uKTsH5oL4Rv8qtVSqQNq/pubhtml

- Scenario #1: Sheet "Hoax analysis"
- Scenario #1-extended: Sheet "Google keyword suggestions"
- Scenario #2: Sheet "Response analysis"

### Evaluation metric
- Good traits
  - quote paragraphs in input text (be specific)
  - suggest ways to fact check
  - identifies emotion and ask user to notice its effect
- Bad traits
  - be assertive about facts (can often be wrong)

### Content and notes
- Open AI 其實有針對如何讓 GPT 做複雜的事情出一份[文件](https://github.com/openai/openai-cookbook/blob/main/techniques_to_improve_reliability.md)，整理相關的 prompt engineering 文獻。
    - 其中，「請 model 先做解釋」與把解釋再拿去當 prompt 的 [chain of thought](https://github.com/openai/openai-cookbook/blob/main/techniques_to_improve_reliability.md#prompt-the-model-to-explain-before-answering) 技巧，讓我想到以前做學習單的時候，會透過一系列問題來請學生作答的感覺。
- 學習單：
    - https://flipedu.parenting.com.tw/article/007966
    - https://mlearn.moe.gov.tw/TeachingPlan/PartData?key=10861
- 請 ChatGPT 每個測試輸出三次，放在 output / response 欄位，來看該 prompt 產出的穩定性。
    - 畢竟 GPT 每次都不同，只能多弄個幾次，比較好判斷回應裡的某些特性，是運氣好有出現，還是穩定出現。
- System 需要的內容
  - 今日日期
  - 使用繁體中文

## Notes after implementation

### 2023/4/2 Release issues

> 如果是純 URL 的話，也是會有 ChatGPT 創造訊息的問題呢
> https://en.cofacts.tw/article/1a84s1vm1wh1x
> 或是看 URL 說故事
> https://en.cofacts.tw/article/2dsgnvf5tv9zm
> https://en.cofacts.tw/article/1nk614t9rcp67
> 我多一句 prompt 跟他說
資訊不足的話就說「資訊不足」好了
> [name=mrorz]
> 
> 愚人節的 ChatGPT 回應
> 但傷腦筋的是，愚人節之外的日子能重複使用這個回應嗎囧
> https://en.cofacts.tw/article/2x200por1zvq8
> 然後是愚人節 + 創造訊息的狀況囧
> https://en.cofacts.tw/article/1t9hir08g8he4
> [name=mrorz]
>
> 當訊息很長，AI 回應就會被截斷
> https://en.cofacts.tw/article/3vp866m6tl507
> [name=mrorz]
> 


- 「資訊不足」判定無效。
  - 試圖先問 AI 對於訊息的掌握度，想做類似 chain of thought 的事情
  - AI 總是對訊息的掌握度很有自信。「沒自信要說ㄛ」『我有 7~8 成把握！』
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_251bdcb54c762dfec8141b5496ece5e4.png)![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bbe5dd8d107098c6d4fda1296e82eb91.png)
  - 很有自信的胡謅了連結內容、進行「分析」，然後給了不低的自信分，中英文 prompt 皆然
  - 降低 temperature 也沒用
- 加長 prompt 失敗
  - ChatGPT 會失去原本節錄 + 列點的特性，變得只會給一般性的回應 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e15ddea4e706f8f744b7f090d150f3f.png)
  - 「切勿杜撰」沒有效果，他根本不認為自己在杜撰 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8cacfb54d276ce16d2736caafdf4dcef.png)
- 把 url-resolver 內容放進去
  - 嘗試分開 URL 與內文。會認為是全文而非摘要，對於「沒有提及⋯⋯」過度武斷 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2245f46a8ce1021a6b9fef7ad1dafd7f.png)
  - 借用 Markdown 語法。影片 description 與影片本身無關的就可能會誤導 AI ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_3b36d72da70f7a82433b8c5e652e6c87.png)
  - 新聞與詐騙能抓到較長內文的還 OK，但不知為何會杜撰網友反應，也有機會給出過於武斷的 assertion ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ddff62bd51481c2641b8306b2aeaee39.png)
  - 降低 temperature 來取得分數最高的回應 (from [FB discussion](https://www.facebook.com/whiskyInsularis/posts/pfbid0rmmeNyvekBxNVJGV6L4GjEsDhsaE3nkJ1B5Sga8jB7iYwDZFyv3UPWYMvNU1BkhMl?comment_id=1369215066982221&reply_comment_id=242943751518840))
- 愚人節問題
  - 把時間模糊化（2023年4月1日 --> 2023年4月）即可。原本給定時間本來就只是想要不讓 AI 覺得現在還在 2019 年而已。模糊到月份應該就能避免「今天是愚人節」的回應。
- Prompt 太長時回應會被截斷

### 2023/4/6 Release issues

> https://cofacts.tw/article/352fgg6gci7f2
> 原文是「如果已經下載了怎麼辦」
> chatgpt：
> 以下是節錄的訊息內容：
> >「最近有一個新的病毒叫做“哈哈病毒”，它會在你的手機上自動下載一個名為“綠色框框”的應用程式，然後竊取你的個人信息。」
>
> 為什麼chatgpt 分析的跟原文好像對不起來？
> [name=cai]

- 看來在 prompt 裡面加一小段有奇效 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4b3224e7123b2c2c46111c8195c07234.png)

>  剛好看到這裡有被 GPT 掰東西 suffer 的問題，我這邊有一些經驗可以分享：
> 1. temp 設的越低的方向是對的，我的使用是直接給他0
> 2. 目前3.5 這版本 doc 有說明，prompt 寫在system 控制的效果不理想，我測試起來也是這樣的感想，建議角色代入的部分就直接移到user 那邊要他做，反正使用的token count 是一起算的
> 3. 如果要他驗證給予的內容，chain of thought 的方式可以大幅增加robustness ，要他自己說明過程，順便回答自己說的是不是正確的
> 4. prompt要他只能使用給予的內容，這部分除了各種強調之外，給予內容跟指令的順序前後，也會大幅影響效果，我自己的經驗是主要第一個指令先寫，再來給予你的內容，後面再補上要限制他的n個指令，不過順序的調整就要試試看，但是順序 matters，這部分和人的直覺比較違背，也算是使用過才知道的 know-how 哈哈
> 以上是我這幾個月使用的心得，希望對你有幫助！
> [name=Chen-Hung, Pai] 

目前的 prompt 是有使用 system，主要指令使用 user，但放在訊息後面。

即使把第一句話換成 user prompt，角色+指令 > 內文 > 限制這個調整好像比目前的順序（角色 > 內文 > 指令+限制）來得差。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_10b9aaf5261dc57b2268a9c86db7f211.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_040529d5f7a28da421690f2bce2249fa.png)

>  https://cofacts.tw/article/1onf7k6inka4f 這篇好多人問，chatgpt 又在亂掰了
>  [name=cai]

似乎有「或懷疑」之後比較不會被帶著走
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9922d8100a47fbc6a6aad6719129890e.png)

> 看起來新版的 prompt (增加不要編造、懷疑的地方) 比較不會附和訊息 [name=mrorz]
> https://g0v.hackmd.io/mU8qi721RZeAQ9PDfj7XRA?both#202346-Release-issues


### 2023/5/17 Year issue

https://cofacts.tw/article/2ift587i48415

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a4d28d26fdf87f5da0c2d19157ee3baa.png)

Solution: add 民國年
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_01562d1b9d4eca5f8db4a632d0a4bed4.png)

### 2023/6 之後的 hallucination

> chatgpt 亂掰實錄+1
> https://cofacts.tw/article/ulqav0m1oszt
> 原文：「這是詐騙嗎，發票根本沒中獎」
> chatgpt：
> 好的，以下是節錄的訊息內容：
> 「恭喜您！您的手機號碼在本期發票中獎，獎金高達100萬元！請點擊以下連結領取獎金。」 [name=cai]
> https://g0v.hackmd.io/dkyaltHuSp6jPPw9oL4Wig#Hallucination

> temperature 調高一點也是如此，所以不是某個不夠好的 local optima ，而是整個 prompt 在這個 input 下表現就是會 hallucinate [name=mrorz]
> ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_45fbf895b6dabfed630e044b6147c719.png)
> 不承認資訊不足 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_257fe79dbf8862652e0cfc5dbf4f72c7.png)

> 亂掰實錄+1
> https://cofacts.tw/article/1snx2bfar14ix
> 亂掰 +2
> https://cofacts.tw/article/2dtzpyrj7b53s
> https://cofacts.tw/article/2df9099tizgfd
> [name=cai]
> 看來 AI reply 還是要文字長一點才生成比較好
> [name=mrorz]


> https://cofacts.tw/article/pwe0vm61ud70
> chatgpt 這次把奧運舉辦地點換地方了www
> [name=cai]