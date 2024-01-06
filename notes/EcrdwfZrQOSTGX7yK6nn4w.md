# Cofacts category review generator design document

This document describes the manual review process of training data fed into Cofacts [rumors-ai-bert](https://github.com/cofacts/rumors-ai-bert) model.

## Traning data generation flow

```
Elasticsearch
--(Script 1)-> spreadsheets
--(Script 2)-> JSON files per article
               Write to Elasticsearch (to be included in next (1) run)
```

The two scripts:
- Script 1: A `rumors-api` script, `genCategoryReview`, that generates an xlsx file of items to review.
- Script 2: A `rumors-api` script, `genBERTInputArticles`, that (a) generates a zip with JSON for each article to train, and (b) writes to Elasticsearch so that the review result will be included in the next run.

Target JSON for one article are as follows, in which  `tags` being the ground truth for the classifier:
```json
{
  "createdAt": "2018-11-14T01:24:49.719Z",
  "hyperlinks": "",
  "id": "1pt6j5jf6s6dq",
  "reference": "LINE",
  "tags": ["lT3h7XEBrIRcahlYugqq"],
  "text": "自中國進口水壺蓋 太和工房被爆驗出殘渣值超標57倍",
  "url": "https://cofacts.g0v.tw/article/1pt6j5jf6s6dq"
}
```

All ground truth labels (category IDs in `tags`) should be "Human reviewed" a.k.a.
- Human tags that is reviewed
- AI tags that is "agreed" by users and is reviewed by users

Categories to *not* put in `tags`:
- Tags (AI / Human) that is not reviewed by anyone.
- Tags (AI / Human) that user that has more "disagreed" than "agreed"

Therefore, we design Script 2 to only include tags with positive scores (article-category feedback score sum) in the resulting JSON's `tags`.

For each `articleCategory`, the scripts would process them in the following logic:
- If the article-category is added by AI:
    ```
    Some user "agrees" (positive articleCategoryFeedback)
    --> Script 1 include it in review
        --(adopted)--> Script 2 adds another "Agree" (positive articleCategoryFeedback)
            --> It has score +2;
                will be included in JSONs
        --(not adopted)--> Script 2 adds a "Disagree" (negative articleCategoryFeedback)
            --> It has score +0;
                will not be included in JSONs
    ```
- If the article-category is added by human:
    ```
    Script 1 include it in review directly
    --(adopted)--> Script 2 adds one "Agree" (positive articleCategoryFeedback)
        --> It has score +1; will be included in JSONs
    --(not adopted)--> Script 2 adds a "Disagree" (negative articleCategoryFeedback)
        --> It has score -1;
            will not be included in JSONs, and
            is not counted as a valid category
    ```
## Script 1. `genCategoryReview` script in `rumors-api`

### Input
Date of `articleCategory` to start scanning for article categories of interest.

### Output
A xlsx file with the following sheets:
- article-category sheet: the article-categories to review
    - article id (vertical merge cell if duplicated with last row)
    - article text (vertical merge cell if duplicated with last row)
    - category title to review
    - other's deny reasons
    - adopt? (User input; used by script 2)
    - deny reason (User input; used by script 2)
- mapping sheet: category ID v.s. category title

:::info
Sample file: https://docs.google.com/spreadsheets/d/1pAd93Lnaa-L1r6r5b7h1E94IDSqvQxmvMN7XvMkQZXE/edit#gid=1075473317
:::

### Execution
- Prepare xlsx file with the sheets
- Loop through all `articleCategoryFeedbacks`, record the following info per article-category:
    - total score
    - latest feedback date by others (not we the reviewers)
    - our (appId = `rumors-ai`, userId = `category-reviewer`) previous vote on this article-reply (if there is any)
    - our deny reason if previously denied (if there is any)
    - negative feedback reasons by others
- Loop through all article:
    - Collect article categories of interest, which is defined as:
        - date criteria
            - creation date >= input date, or
            - latest feedback date by others (not we the reviewers) >= input date
        - created by website user, or created by AI (has `aiModel`) with positive total score
    - skip the article if there is no article categories of interest
    - add a row to the article-category sheet for each article categories of interest
        - Auto fill true in "adopt?" if previously adopted
        - Auto fill out deny reason in "deny reason" if previously denied
- After the xlsx file is generated, we can manually import it to Google sheet and start human reviews.


## Script 2. `genBERTInputArticles` script in `rumors-api`

### Input
- A public google sheet ID

### Output

1. Write review results (adopted / deny reason) to ElasticSearch as `articlecategoryfeedbacks`.
    - Entry appId: `rumors-ai`
    - Entry userId: `category-reviewer`
3. A zip file of JSON in the following format:
    ```json
    {
      "createdAt": "2018-11-14T01:24:49.719Z",
      "hyperlinks": "",
      "id": "1pt6j5jf6s6dq",
      "reference": "LINE",
      "tags": ["lT3h7XEBrIRcahlYugqq"],
      "text": "自中國進口水壺蓋 太和工房被爆驗出殘渣值超標57倍",
      "url": "https://cofacts.g0v.tw/article/1pt6j5jf6s6dq"
    }
    ```

### Execution

1. Validate sheet
    - Validate the mapping sheet is identical to the current database's.
    - If not, user should fix the spreadsheet so that trained model can be used on production
    - Validate all added / removed category in the article-category sheet are inside the mapping sheet
2. Write info in sheet to Elasticsearch
    - Group rows in article-category sheet by article ID
    - Record `latestArticleCategoryCreatedAt`, which is the latest `createdAt` timestamp among all article-category in sheet
    - For each adopted categories: Write / update positive `articleCategoryFeedback`
    - For each denied catategories: Write / update negative `articleCategoryFeedback`
    - Update vote count in article-category
3. Generate article JSON files
    - Scans through all articles
    - put article-categories with at least 1 upvote in `tags` in the JSON
        - Skip new article-categories with `createdAt > latestArticleCategoryCreatedAt`. These article-categories are created after Script 1 is run and is not reviewed yet.
    - If `tags` array is not empty, emit 1 JSON file for the article

## Future TODO

1. Fix old categories such as AIDS
2. Subgroup category handling
    - e.g. If the article has COVID-19, add 醫藥
    - Maybe it should be implemented as part of application logic, i.e. 醫藥 is added automatically when the article is marked as COVID-19 or AIDS.
