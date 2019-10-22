# ttParser
可用于字节跳动小程序富文本处理

### 步骤一
将ttParser移动到根目录下

### 步骤二
ttss文件中处理数据并注入html
```
let that = this;
let ttParser = require('../../ttParser/index');
ttParser.parse({
    bind: 'richText',
    html: html,
    target: that,
    enablePreviewImage: false,
    tapLink: (url) => {}
});
```
- img标签需要特殊处理，根据后端给到的数据手动修改url匹配的字段，以及height和width
- 如出现未匹配到的标签，如<span+字体等，需要手动过滤

### 步骤三
ttml文件中插入
```
<import src="../../ttParser/index.ttml"/>
<view class="wxParser">
    <template is="wxParser" data="{{wxParserData:richText.nodes}}"/>
</view>
```