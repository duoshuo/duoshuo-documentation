## 获得当前文章评论数和转发数接口

### GET `/threads/counts.json`
  - `short_name`* `<String>` 站点注册的多说二级域名
  - `threads`* `<String>` 你需要获取的文章的 `thread-key`, 如有多个 `thread-key` 以逗号分割。例如：`4ff160411318693231000006,4ff160411318693231000007`

#### 请求范例
```bash
$ curl -X GET \
  http://api.duoshuo.com/threads/counts.json? \
  short_name =  official& \
  threads    =  4ff1cbc43ae636b72a00001d
```

#### 返回范例
```js
{
  response: [{
      thread_id: "3674083",
      thread_key: "4ff28d95552860f21f000010",
      comments: 20,
      reposts: 0,
      likes: 0,
      dislikes: 0,
      views: 600,
      weibo_reposts: 1,
      qqt_reposts: 1
    }
  ],
  options: {
    comments_zero: "暂无评论",
    comments_one: "1条评论",
    comments_multiple: "{num}条评论",
    reposts_zero: "暂无转发",
    reposts_one: "1条转发",
    reposts_multiple: "{num}条转发"
  },
  code: 0
}
```

#### 返回参数
- `code` `<Int>` 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` `<String>` 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` `<Object|Map>` 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。
- `thread_id` `<String>` 文章在多说数据库中的 ID
- `thread_key` `<String>` 文章在原站点中的 ID 或其他唯一标识
- `comments` `<Int>` 文章评论数
- `likes` `<Int>` 文章被点「喜欢」的次数
- `views` `<Int>` 文章被阅读数
- `weibo_reposts` `<Int>` 文章的新浪微博转发数
- `qqt_reposts` `<Int>` 文章的腾讯微博转发数
