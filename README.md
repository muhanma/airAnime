因为感觉经常在各视频网站找番有点浪费时间，于是就突然萌生了一个想法：如果能同时进行，就不会浪费太多时间了。所以，airAnime就出于这个想法诞生了。

airAnime是一款聚合「番剧&动漫搜索」程序，借助于各网站的数据及各网站的搜索功能进行指定搜索，以减少搜索番剧的时间。

Demo: [airAnimeOnline](http://airanime.applinzi.com/).

以下是代码说明块。

代码说明
==========================

## 代码结构:

```
.
├── .css
├── .images
├── .js
├── .functions
    ├── .chttochs - 繁体与简体转换代码
    ├── function.php - 封装的通用功能性代码
    ├── mains.php - 程序主要功能代码
    ├── pages.php - 输出通用网页部分代码
    ├── srhauto.php - 获取关键词联想结果代码
    ├── bangumiinfo.php - 获取番剧信息代码
    ├── bangumiSug.php - 番剧推荐代码
    ├── bangumiS.json - 2000年至今(2017/2/4)的日本动漫信息
    ├── bangumiS2017.json - 新番放送表(2018年冬)
    ├── bangumiToday.json - 动漫推荐缓存文件
├── .d
    ├── .server - 放于其他服务器的文件
    ├── index.php - InfoDownload主代码
    ├── list.js - 列表搜索功能JS
├── .pages
    ├── about.php - 关于页面
    ├── start.php - 使用文档页面
    ├── if.php - 数据源可用性页面
    ├── srhcode.php - 搜索指令页面
    ├── notice.php - 告示页面
├── index.php - 程序主代码
├── run.php - AJAX接受数据并处理

```

## 细节
### 番剧推荐
设计思路是这样的：

自已更换bangumi动画id→执行更新数据(访问 url/functions/bangumiSug.php/?code=up )→数据保存到本地。程序只是调用本地数据。

id获取代码在 functions/bangumiSug.php 25-27行。百度翻译API授权于 'index.php'266,267行。

### Fonts
字体链接位于 '.css' 4个.css后缀文件中。默认使用我的七牛CDN，但这存在风险，万一我哪天突然换了是吧，所以请请自行修改。字体位于 '.css/Roboto' (请注意更改css.css的代码)。

### PicSearch(以图搜番)[beta]
已开放测试此功能，用 !image:?; 指令使用，限制为 10次/min 。具体请参考 搜索指令 页面。自行搭建前请务必修改 贴图库与whatanime.ga 的token，分别位于 'index.php'97行 与 'functions/mains.php'471行。

### Type类型
本程序的搜索内容类型分为: 二次元 Anine(动画),Comic(漫画),Novel(小说),Download(下载).

Anine包含如下数据源: Bilibili(哔哩哔哩),Dilidili(嘀哩嘀哩),Fcdm(风车动漫),PPTV(聚力),Letv(乐视),iQiyi(爱奇艺),Youku(优酷),TencentTV(腾讯视频),BaiduAll(百度集合搜索).

Comic包含如下数据源:DMZJ(动漫之家),BKMH(布卡漫画),DMW(动漫屋),TKMH(图库漫画).

Novel包含如下数据源:DMZJ(动漫之家),TXDM(腾讯动漫).

Download包含如下数据源:MGJH(蜜柑计划).

搜索以上信息包含三种方式:  
* 站内搜索 -抓取网站内提供的搜索信息，所以相对较准确。
* 百度协助搜索 -在一些站内搜索速度慢或者不怎么推荐的数据源或者没办法直接抓取的数据源会使用这种方法，因为取百度搜索结果，并且用正则只匹配一种规则，所以匹配结果范围较大。
* 集合搜索 -抓取百度工具的集合番剧信息，不过匹配码只针对一些例子，所以时有时无。

## 更新日志

#### v1 RC2!
* 新增 Bangumi图片镜像
* 完善 界面
* 更变 头图

#### v1 RC2
* 全新 主页
* 新增 番剧推荐
* 新增 新番放送表
* 新增 简单余弦相似度算法[DILIDILI数据源开启测试]
* 完善 番剧信息获取功能

#### v1 RC1.2
* 修补 累计的细节及BUG
* 新增 搜索内容推测算法
* 开启 番剧信息获取功能
* 进入 更新休眠期(上学中)

#### v1 RC1
* 修补 细节及BUG
* 新增 漫画源
* 待定 部分功能(源码中注释掉的部分)
* 进入 更新休眠期(要上学惹)

#### v1 beta5
* 优化 InfoDownload界面
* 新增 InfoS(动漫信息搜索)[beta,未开放]
* 新增 漫画源(图库漫画)
* 新增 AJAX异步数据提交
* 新增 PicSearch(以图搜番)[beta]

#### v1 beta4
* 优化 百度协助搜索-漫画(精度提高约至92%)
* 优化 InfoDownload(数据基于蜜柑计划)[beta]
* 新增 小说源(动漫之家,腾讯动漫)
* 新增 漫画源(动漫屋)
* 新增 背景图与毛玻璃效果
* 待定 以图搜番测试版[未开放]

#### v1 beta3
* 优化 指令搜索代码结构
* 优化 百度协助搜索(精度提高约至90%)
* 新增 image[未开放],type指令
* 新增 漫画搜索(动漫之家,布卡漫画)
* 新增 以图搜番测试版[未开放]

#### v1 beta2
* 优化 内部代码结构
* 优化 百度协助搜索规则(更加精准稳定)
* 优化 页面载入速度
* 新增 腾讯视频数据源
* 开启 动漫花园下载数据源测试
* 开启 短网址:airs.im

#### v1 beta1
All

## 声明
本程序源代码可任意修改并任意使用，但禁止商业化用途。一旦使用，任何不可知事件都与原作者无关，原作者不承担任何后果。

如果您喜欢，希望可以在页面某处保留原作者(Trii Hsia)版权信息。

感谢。

Feb 4th,2018  
Trii Hsia