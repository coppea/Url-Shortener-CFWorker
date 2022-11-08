使用Cloudflare Worker创建的URL缩短器｜支持自定义首页｜支持Menu Short｜支持短网址和文本分享

**首页**

<img width="800" alt="首页" src="https://user-images.githubusercontent.com/86509331/199412206-b4aa8b77-ab4c-4328-8143-cc7e0974a235.png">

**后台**

<img width="800" alt="后台" src="https://user-images.githubusercontent.com/86509331/199411957-aa39205b-d9c1-4b3a-b9bb-26d1aed824b2.png">


## 常量设置
```js
const admin_path = '/admin_err24d' // 访问地址，如果需要公开访问,把`/admin_err24d`设置成`/`即可
const api_path = '/vcfgbn_api'  //Short Menu第三方访问api，建议设置复杂
const url_key = 'longUrl'  //原始长链接
const url_name = 'shortCode' // 自定义后缀  
const short_url_key = 'shorturl';   //完整缩短后链接，'shorturl'是为了兼容Short Menu
```
网址响应
```js
{
 "longUrl":"https://abc.com",
 "shortCode":"dfcw",
 "type":"link",
 "shorturl":"https://url.com/dfcw"
}
```
文本响应
```js
{
 "longUrl":"这是测试文本",
 "shortCode":"dfce",
 "type":"text",
 "shorturl":"https://url.com/dfce"
}
```
## 自定义首页[index.js](../383fc4a0d8de613c02f5a3f4de048a06ce7004cb/index.js#L163)

```js
const statichtml = "https://raw.githubusercontent.com/bituplink/OneHtmlNav/master/goodweb.html"
```
修改上方网址为自己喜欢的网址，只支持单html，建议css和js和script集成进html里

-------
## [cloudflare Work](https://dash.cloudflare.com)

### 去Workers KV中创建一个命名空间

<img width="1020" alt="去Workers KV中创建一个命名空间" src="https://user-images.githubusercontent.com/86509331/199402623-677c28da-f5de-42d0-b7f9-b652c89f0311.png">


### 去Worker的设置选选项卡中绑定KV 命名空间
<img width="1020" alt="绑定KV Namespace 1" src="https://user-images.githubusercontent.com/86509331/199405088-38963240-e967-4a69-921e-f06299d403c1.png">


<img width="1020" alt="绑定KV Namespace 2" src="https://user-images.githubusercontent.com/86509331/199405413-c117ed63-2cf9-4fad-a89e-327cc7b137c2.png">


### 其中变量名称填写`shortlink`, KV 命名空间填写你刚刚创建的命名空间

<img width="1020" alt="绑定kv" src="https://user-images.githubusercontent.com/86509331/199404159-9e3c14e9-22ca-4957-958f-19f9ab0af105.png">


### 复制本项目中的[index.js](/index.js)的代码到Cloudflare Worker 

### 点击保存并部署

-------

### Short Menu设置截图

![Upic设置](https://user-images.githubusercontent.com/86509331/199400317-929ee122-b5d0-4cb6-9e9b-0362cb6afbd4.PNG)
---------
## 短链接来自于[@xyTom](https://github.com/xyTom/Url-Shorten-Worker)和[@code-scan](https://github.com/code-scan/cfwork_shortlink_text)
## 自定义首页来自[@bituplink](https://github.com/bituplink/OneHtmlNav)
