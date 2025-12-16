# 20251216 會議記錄

:::info
- [所有會議記錄](https://g0v.hackmd.io/@cofacts/meetings/x232chPbTfGgNL_Q0f47rQ)
- NPO Hub 出席：
- 線上出席：
- https://meet.google.com/mrz-dgrd-pri
:::

## :potable_water: Release pipeline

### :rocket: Staging

#### :globe_with_meridians: Site

- Update package-lock.json and package.json for node version and cross-env by @chennjustin in [#620](https://github.com/cofacts/rumors-site/pull/620)
- fix: Redirect to new user profile URL after the user removes their slug settings #563 by @YUHUIYI in [#615](https://github.com/cofacts/rumors-site/pull/615)

Test if changing URL slug does not redirect user to correct place.


## :eyes: 上次會議跟進事項

*   **[Epic] Elasticsearch Migration**
    *   改 API
    *   驗證資料是否正常
        *   記錄一下 reindex 所需時間
        *   reindex 時 elasticsearch 會用多少記憶體
    *   上 staging
* GCP cost
    - 半個月過去
    - 剛好花 230 的一半 ![](https://g0v.hackmd.io/_uploads/HkaoA5AMbg.png)
* Error rates
    - Error on 12/14 only
    - From LINE: the error was true. ![](https://g0v.hackmd.io/_uploads/BygD9GsAMbe.png)



## Pull Request Reviews

- **cofacts/beta-ai#11: Update ADK to 1.21**
  - `gemini-code-assist[bot]` submitted a review.
  - https://github.com/cofacts/beta-ai/pull/11#pullrequestreview-3581376063

- **cofacts/rumors-site#615: fix: Redirect to new user profile URL after the user removes their slug settings #563**
  - `MrOrz` submitted a review.
  - https://github.com/cofacts/rumors-site/pull/615#pullrequestreview-3557292962
