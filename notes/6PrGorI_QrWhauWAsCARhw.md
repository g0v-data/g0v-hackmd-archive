# Taiwan Politics Open Data(TPOD) - draft
- Dataset maintained by 台灣資訊環境研究中心 [IORG](https://iorg.tw/_en/about)
- See also: [https://iorg.tw/doc/tpod](https://iorg.tw/doc/tpod) (zh-tw)

## Open Data Scope
This dataset include two kinds of data:

1. The information of 2024 presidential candidates, legislative candidates, list of at-large legislators, and other political entities in Taiwan.
2. The Facebook page posts we collected according to the list we mentioned above, since 2020 and accompanying metadata.

For more comprehensive list of political entities see this [Google Spreadsheet(zh-tw)](https://docs.google.com/spreadsheets/d/1PMhykVROyduS-yZS8Xdt0zB2_GGBTxowsej0PRnWwM0/edit?usp=sharing). Ｗe uplopaded the dataset to [HuggingFace-private]() to save researchers the steps of applying for data.

### Author
| Field               | Description                                                           |
|---------------------|-----------------------------------------------------------------------|
| author_id           | Id of Facebook fan page or personal Facebook account                  |
| party               | The party name for this political entity belong to                    |
| name                | Name of political entity, not the name of Facebook fan page           |
| title               | Name of role, position title, occupation                              |
| electoral_district  | Electoral district of 2024 election                                   |
| url                 | Link to Facebook fan page or personal Facebook account                |





### Docs

The filenames of the CSV files in the docs folder are all named after the author_id, following the naming convention：{author_id}.csv.

| Field                | Description                                   |
|----------------------|-----------------------------------------------|
| doc_id               | Facebook doc id                               |
| doc_published_at     | Publish time of the Facebook doc              |
| doc_url              | Link to the Facebook doc                      |
| doc_text             | Content of the Facebook doc                   |
| doc_type             | Type of the doc(post, link, photo, video, share... etc) |
| doc_reaction_count   | Count of all kinds of reaction(like, angry, haha... etc) |
| doc_comment_count    | Count of comment                              |
| doc_share_count      | Count of share                                |
| doc_like_count       | Count of reaction: 👍 like                    |
| doc_angry_count      | Count of reaction: 😡 angry                   |
| doc_haha_count       | Count of reaction: 😆 haha                    |
| doc_love_count       | Count of reaction: 🥰 love                    |
| doc_sad_count        | Count of reaction: 😢 sad                     |
| doc_support_count    | Count of reaction: 🤗 support                 |
| quote_url            | Shared link in the doc                        |
| quote_title          | Title of shared link                          |
| quote_text           | Text of shared link                           |
| quote_type           | Shared type                                   |

