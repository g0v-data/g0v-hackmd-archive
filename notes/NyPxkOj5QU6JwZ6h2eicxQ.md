有問題一起列


/~~/ TODO: OK 1 /v1/Members/Home/Categories add ParentId 第一層的 全部 改拿掉~~
// TODO: ~~查詢統計都一起加 video 全加到 post 裡~~
// TODO: 加智慧搜尋 by tag


~~1 player video 喜歡 , 喜歡數, 收藏, 收藏數, 評論數~~ 
~~2 QueryPostHandler 截掉Content 60字 PostType text 才截~~
~~3 Post 移掉 status, 上下架, 原因, 修改者, 時間~~
~~4 me query 我的收藏 ~~
~~5 post IsMemberFollow~~
~~6 Club IsClubFollow~~
~~7 query post 加搜尋 key~~
~~8 member/me/playlist 喜歡 , 喜歡數, 收藏, 收藏數, 評論數 ~~
~~9 remove members/video/{videoId}/Comment~~
~~10 取得我的短視頻收藏列表~~
~~11 我的帖子列表




// From iOS & Android
1. Category 第一層的”首頁”由前端 hardcode, 第二層之下的”全部”由 api 給
2. 成人 Category 第一層標籤(圈子,短文,照片,短視頻) 之後會由 Category API 提供
3. 廣告 App 常寬比 1:7, 要可以跟著 scroll view 滑動 
4. 搜尋頁：熱門搜尋 tag 暫時不需實作
5. 成人首頁&排行榜的”密密視頻”從 statistic 拿，其他的（短視頻，貼文等）從 PostStatistics (ios note
6.  Content data model 最大化待議  （https://drive.google.com/file/d/1B_mOXuZfFpfoAwDOkaYp2MtmIElfXDgZ/view）
7. 圈子列表內 需加入圈子是否被關注
8. 我的關注內目前有關注個人，需在加入關注的圈子
9. 評論回復評論最多兩層，子評論回覆子評論只需代入第一層parentID, 需@對方名字 + 評論內容
10. Post 的 title ＆content 字數會縮短，進到Detail頁需要在打 Detail API 取得完整內容
11. Swagger 上面打api，X-Requested-From 欄位要帶 “web”， id 型態為字串，來避免前端的進位問題
12. 短視頻與影片才可以蒐藏，但尚無短視頻的蒐藏列表 API
13.  pm會再確認我的收藏是否新增短視頻tab
14.  Post 內會再添加發文者或圈子是否已關注 flag
15. Video play 頁面的 comment 由 get: member/post/{postId}/comment 來，postId 代 videoId
16. post: Member/video/{videoid}/comment 會由 post: member/post/{postId}/comment 取代 postId 代 videoId
17. Video 下的 like數, 蒐藏數，評論數會添加在 videoInfo ＆ playlist 內
18. Post: member/post/{postId}/like 回傳500 會再修正






