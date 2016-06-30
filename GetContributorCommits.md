## 获得contributor的贡献（commit 数）

**参考：** 
[链接](https://developer.github.com/v3/repos/statistics/)

**语法：**

```bash
GET /repos/:owner/:repo/stats/contributors
```

**例子：**

```bash
https://api.github.com/repos/twbs/bootstrap/stats/contributors
```

> **注意：** 这个请求所有信息都在第一页，所以只取第一页就可以。这样即使有100个Repositories，也只消耗100个GitHub API request。

**回复：**

```
[
	{
		"total": <总commit数>,
		"author": {
			"login": <contributor_1 的名字>，
			"url": <URL>,
			……
		},	
		"weeks": [每个星期的贡献，我们不需要这个数据]
	},
	{
		"total": <总commit数>,
		"author": {
			"login": <contributor_1 的名字>，
			"url": <URL>,
			……
		},	
		"weeks": [每个星期的贡献，我们不需要这个数据]
	},
	……
]
```

我们只需要抽取`author.login`、`author.url`和`total`就可以知道contributor的信息以及对应的commit数了。最后针对每个contributor都可以可以建立下面的JSON object。

```
{
	"contributor": <author.login>,
	"url": <author.url>,
	"total_commits": <total>
}
```

**效果图：**

最后，拿到这些数据以后，我们也可以做出这样的效果图。
![效果图](https://qph.ec.quoracdn.net/main-qimg-f2c410f9ac5119a1eb9c867c8b7a72e1?convert_to_webp=true)
