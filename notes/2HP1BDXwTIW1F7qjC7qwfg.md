A short summary of : 
* Zhou and Zafarani, A Survey of Fake News: Fundamental Theories, Detection Methods, and Opportunities (here’s a podcast version) 
* Zhou and Zafarani, Fake News Early Detection: An Interdisciplinary Study


## Summary

### Defining Fake News

* Aspects
    * Authenticity
    * Intention
    * News or not News
* Fake news is intentionally false news published by a news outlet.
* Other concepts
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_60aed3bfc631758f4f4219e1c02415b4.png)

* Click-bait
_[Fake News Early Detection: An Interdisciplinary Study]_
_"Clickbait is the headlines whose main purpose is to attract the attention of readers and encourage them to click on a link to a particular Web page….To achieve the purpose, clickbait creators make great efforts to produce an information gap [28] between the headlines and individuals’ knowledge. Such information gaps produce the feeling of deprivation labeled curiosity, which motivates individuals to obtain the missing information to reduce such feeling."_

### Detecting Fake News

1. Knowledge-based (fact-checking)
    - Manual (By credible institution or by crowdsourcing)
    - Automatic

2. **[Automatic] Style/Content-based**
    - Can analyze the **intention**, in addition to authenticity, of such piece of info

        _"knowledge-based methods mainly evaluate the authenticity of the given news, while style-based methods can assess news intention, i.e., is there an intention to mislead the public or not? The intuition and assumption behind style-based methods is that malicious entities prefer to write fake news in a “special” style to encourage others to read and convince them to trust."_

    - _[Fake News Early Detection: An Interdisciplinary Study]_

        _"Fundamental theories in psychology and social science have revealed some linguistic cues when a person lies compared to when he or she tells the truth. For example, Undeutsch hypothesis [55] states that a statement based on a factual experience differs in content style and quality from that of fantasy; reality monitoring [24] indicates that actual events are characterized by higher levels of sensory-perceptual information; four-factor theory [67] reveals that lies are expressed differently in terms of emotions and cognitive processes from truth; and information manipulation theory [30] validates that extreme information quantity often exists in deception."_
    - Modeled as a ML classification problem.
        - Features could be:
            - Basic Text Features
                - Lexicon-level: standardized BOW (standardized by content-length)
                - Syntax-level:
                    - Shallow: (standardized) frequency of POS tags
                    - Deep: (standardized) frequency of rewrite rules, obtained by Probability Context Free Grammar (PCFG) parsing tree. 
                - Discourse-level: (standardized) rhetorical relationships formed by RST parser.
                - Semantic-level:
                    - (e.g.) Sensationalism
                        **measure the frequencies of positive words and negative words within a news headline by using LIWC,** as well as the news headline sentiment polarity by computing the average sentiment scores of the words it contains.
                    - Punctuations
                    - Similarity between headlines and body-text (existence of information gap)
                    - (e.g.) Quality/Informality
                        LIWC provides five dimensions to evaluate such informality of language: (1) swear words (e.g., ‘damn’); (2) netspeaks (e.g., ‘btw’ and ‘lol’); (3) assents (e.g., ‘OK’); (4) nonfluencies (e.g., ‘er’, ‘hm’, and ‘umm’); and (5) fillers (e.g., ‘I mean’ and ‘you know’). Hence, we measure the informality for each news headline by investigating its word or phrase frequencies within every dimension and include them as features.
                    - Subjectivity
    Benefiting from the work done by Recasens et al. [44], which provides the corpus of biased lexicons, here we evaluate the subjectivity of news articles by counting their number (proportion) of biased words. On the other hand, factive verbs (e.g., ‘observe’) [20] and report verbs (e.g., ‘announce’) [44], as the opposite of biased ones, their numbers (proportions) are also included in our feature set, which are negatively correlated to content subjectivity.
                    - ... 
            - Latent Text Features (word embeddings)
            - Image Features
        - Models:
            * Traditional ML model (SVM, RF, XGBoost)
            * Deep Learning
                * CNN, RNN, … 
                * Event Adversarial Neural Network (EANN) for Explanablility
        * Known Results:
        [Reza Zafarani, Xinyi Zhou, Kai Shu, and Huan Liu. 2019. Fake News Research: Theories, Detection Strategies, and Open Problems.]
    Results indicate that when predicting fake news using a traditional ML framework,
    (1) non-latent features often outperform latent ones; 
    (2) combining features across levels can outperform using single-level features; and 
    (3) standardized frequencies of lexicons and rewrite rules better represent fake news content style and perform better (while more time-consuming to compute) than other feature groups.

    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_69043e56c6a3a7626e77e252f2f7738a.png)


    - Patterns of Fake News Content Style
    
        Some patterns of fake news content (text and images) style are distinguishable from those of the true news. Recent studies have revealed such patterns [Jin et al. 2017; Zhou et al. 2019a]. Particularly,

        - Fake news text, compared to true news text as shown in Fig. 7, has **higher (i) informality (% swear words), (ii) diversity (% unique verbs), (iii) subjectivity (% report verbs), and is (iv) more emotional (% emotional words)**; and

        - Fake news images, compared to true news images as illustrated in Fig. 8, often have higher clarity and coherence, while lower diversity and clustering scores (see Table 5 for a description of these features).

3. [Automatic] Propagation-based
    - 3 life stages: being created, being published, being spread (on social media).
        * Main challenges: cannot detect fake news at its early stage, but early detection is particularly crucial for fake news, 
            * the more a piece of news is spread, the more users trust it
            * it has been demonstrated that it is difficult to correct one’s cognition after fake news has gained their trust (i.e., Semmelweis reflex, confirmation bias, and anchoring bias).
        
4. Source-based
    
### Open issues
    * fake news early detection
    * check-worthy content identification
    * cross-domain/topic/language study of fake news
    * representation learning for fake news detection
    * fake news intervention
### Thoughts and Future Work
1. A well-established benchmark dataset for fake/real news and/or different concepts of news
    * Jeppe Nørregaard, Benjamin D Horne, and Sibel Adalı. 2019. NELA-GT-2018: A Large Multi-Labelled News Dataset for the Study of Misinformation in News Articles. In Proceedings of the International AAAI Conference on Web and Social Media, Vol. 13. 630–638.
        * https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ULHLCB
        
    * CHECKED: Chinese COVID-19 Fake News Dataset 
        * http://arxiv.org/abs/2010.09029
        * https://github.com/cyang03/CHECKED

    * BuzzfeedNews: a small dataset of news articles that had high Facebook engagement during the 2016 U.S. Presi- dential Election. The dataset contains 1627 articles that are fact-checked by 5 Buzzfeed journalists.
        * github.com/BuzzFeedNews/2016-10-facebook-fact-check
        
    * FakeNewsCorpus: containing nearly 10M articles labeled using opensources.co. OpenSources is a list of sources la- beled by experts. These labels include 13 different labels related to the reliability of the source
        * github.com/several27/FakeNewsCorpus
        
    * LIAR is a fake claim benchmark dataset that has 12.8K fact-check short statements from politifact. com (Wang 2017)
    * Kai Shu, Limeng Cui, Suhang Wang, Dongwon Lee, and Huan Liu. 2019. dEFEND: Explainable Fake News Detection. In Proceedings of the 2016 IEEE/ACM International Conference on Advances in Social Networks Analysis and Mining. IEEE Press.
    * FakeNewsNet: Kai Shu, Deepak Mahudeswaran, Suhang Wang, Dongwon Lee, and Huan Liu. 2018. FakeNewsNet: A Data Repository with News Content, Social Context and Dynamic Information for Studying Fake News on Social Media. arXiv preprint arXiv:1809.01286 (2018).
    * Kai Shu, Suhang Wang, and Huan Liu. 2019. Beyond news contents: The role of social context for fake news detection. In Proceedings of the Twelfth ACM International Conference on Web Search and Data Mining. ACM, 312–320.
* Patterns of RG 可疑訊息
* Which “concepts” does the RG 可疑訊息 belongs to