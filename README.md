# zhihu-api-generator

#### Ver 3.00

使用zag生成你的专属API*。

[^*]:需要云服务支持



## 什么是 zhihu-api-generator ？

zhihu-api-generator是多个基于JavaScript DOM的脚本，通过DOM方式将你的知乎创作内容导出为json格式的API文档，其中包括了标题，链接，题图等信息。

## 如何使用zhihu-api-generator？

和其他的JavaScript脚本一样，你需要使用浏览器的调试功能执行这些脚本。

**首先，你需要访问到你的个人主页。**

知乎的个人主页一般为：

*www.zhihu.com/people/你的个人域名*

如果你不清楚你的个人域名，你可以从首页右上角头像处，访问“我的主页”。

**切换到对应脚本内容的选项卡**

zag只能在对应选项卡下工作。

*如果你期望导出其他的内容，请务必仔细阅读注释并修改相关内容*。

**在该选项卡下，通过调试执行脚本，浏览器将会自动下载一个名为*用户名.json*的文件。**

回答：https://github.com/LikeDreamwalker/zhihu-api-generator/blob/master/answer.js

文章：https://github.com/LikeDreamwalker/zhihu-api-generator/blob/master/article.js

专栏：亟待更新

动态：亟待更新

示例：

```json
[
    {
        "name": "如何看待黑尾酱在家中挂「东亚病夫」牌匾？",
        "url": "https://www.zhihu.com/question/388466195/answer/1161408857",
        "dateC": "2020-04-17T18:49:25.000Z",
        "dateM": "2020-07-23T03:21:56.000Z",
        "upvoteCount": "5928",
        "commentCount": "290",
        "img": "",
        "text": "曾经听说过一套从天而降的掌法， 今天算是受教了。 我一直想不明白为什么会有人做这种事。 你说这是立场吧，挂在家里不让人知道。 你说这是信仰吧，平时藏的这么严也不展现出来。 恰饭，这怎么恰，这肯定是把自己饭碗扔了。 你要挂挂个笑川天皇， 或者挂个什么模型，表示工匠精神。 或者挂个什么意识形态明显的字， 挂个和哪个宗教人物或者自由斗士的合照…",
        "status": false,
        "statusB": true
    },
    {
        "name": "如何看待青海失联女大学生黄雨蒙疑吞食安眠药自杀？",
        "url": "https://www.zhihu.com/question/411447989/answer/1379792074",
        "dateC": "2020-08-02T17:49:47.000Z",
        "dateM": "2020-08-09T15:00:27.000Z",
        "upvoteCount": "2124",
        "commentCount": "360",
        "img": "https://pic4.zhimg.com/v2-1d04f95c8eefb9c4f8ce14453f02c2bd_bh.jpg?source=c8b7c179",
        "text": "说个不好听的，自杀，你难道还能给自己安排好后事吗？ 你能把葬礼安排好就不错了，你还指望安排好谁给你收尸在哪火化用什么骨灰盒？ 你给殡仪馆说这些你确定人家不会报警救你？来救你了你还能自杀？ 那些站在楼顶桥边被…",
        "status": false,
        "statusB": true
    },
    ...
```

## zhihu-api-generator合法吗？

正如所有的爬虫，API等等内容，请确保你在相关用户协议的规范下使用你获取的内容。

由于zhihu-api-generator使用DOM进行操作，获取的是公开可获取且已经加载在用户端的内容，所以我不认为这会导致违法行为。

但是，请不要将此脚本用于非你创作的内容，也不要将此脚本获取的内容用于商业目的，我不承担由于使用此脚本所造成的一切责任。

## 已知问题 与 版本更新：

Ver 3.10:

**现在，zag将以独立文件的方式存在**

·**[新增]**answer.js, article.js

·**[回调]**调整回调函数的延迟为100ms

·**[BUG]**我没能修复undefined错误，但是undefined错误在一定情况下并不会影响脚本的正常运行。同时在大量测试中（450+回答）捕获数量略少，原因不明。

Ver 3.00:

**重构代码，现在以更高效的方式运行**

·**[新增]**每个对象加入默认值为false的status属性，加入默认值为true的status属性，便于特殊用途

·**[新增]**现在zag可以捕获到你的所有内容，而不再是当前页的内容* 

[^*]:严格来说，是从当前页递归下去，所以请确认在执行脚本前你已经跳转至第一页

·**[新增]**当脚本执行完毕后，用户可以阅读到更为美观的提示内容

·**[新增]**现在脚本会在执行完毕后提供内容预览

·**[BUG]**受限于网络环境与浏览器性能，你可能会遇到getElementByAttr()为undefined错误而导致脚本崩溃，此种情况发生的原因是当脚本进行页面跳转时浏览器并没有加载出对应的DOM内容。在此版本，已经为回调函数设置了1000ms的延迟以充分加载DOM，如果你依然遇到此问题，请考虑更换浏览器或者网络环境，或者依据注释内容适当增加该数值。过高的数值可能会导致性能下降。

Ver 2.00:

（该版本未发布）

·**[新增]**保存为数组而不是类数组，便于遍历

·**[回调]**不再为对象提供length属性

·调整了执行顺序，在得到用户确认之前不会执行下载操作

Ver 1.20: 

·**[新增]**保存为类数组而不是对象，便于Vue等框架的遍历

·**[新增]**增加了length属性，默认值为文章数

·修改了对象内各个对象的命名方式

Ver 1.10:

·**[新增]**增加了获取预览内容的功能（text）

·增加了了更多提示

Ver 1.00：

·**[BUG]**如果你的题图是.png格式的透明文件，知乎有可能在服务器上同时生成了白底与源文件两个文件，当你通过zhihu-api-generator生成json文件后，仅能访问到前者。如果你的站点使用暗色主题或者夜间模式，有必要考虑使用其他来源的.png文件替换知乎源文件。

