# MLINK
m站通过按钮打开APP当前页

> ###### 直接使用已有的 魔窗mLink JS集成文档，文档地址：http://www.magicwindow.cn/doc/mlink-js-api.html


## 1.0.0
-  页面的head中添加配置对象
-  跳转APP按钮必须是a标签，且必须加 class="*app_open_mlink*" 
-  页面body中调用js文件： <script src="https://s.kcimg.cn/public/mlink.1.0.0.min.js"></script>

## 1.0.1
-  页面后加载标签获取
-  页面body中调用js文件： <script src="https://s.kcimg.cn/public/mlink.1.0.1.min.js"></script>

### 初始化

```

 <script>
    // 楼中楼页面只传 type 即可
    var MLINK_DATA = {
        type:"news",    // 页面类型
        id:'81263'      // 页面id
    }
 </script>
```
### 各文章type值
页面 | type
---|---
文章 | news
视频 | video
图集 | image
论坛 | bbs
楼中楼 | doublefloor

### 魔窗mLink JS

- 短链为后台配置生成的固定链接，必填参数
```
var link = 'https://anwka9.mlinks.cc/AcRD';//短链地址
```

- 初始化mlink

> 只有楼中楼比较特殊 id=window.btoa(location.href) 将当前页面路径转为base64；title=encodeURI(document.title) title标题编码

```
new Mlink({
    mlink:'https://anwka9.mlinks.cc/AcRD',//短链地址
    button:document.querySelector('a#btnOpenApp')
});
/* ------ 或 -------- */
var link='https://anwka9.mlinks.cc/AcRD';//短链地址
var options = [
    {
        mlink: link+'?type=news&id=81263',
        button: document.querySelector('#openNews')
    },
    {
        mlink:link+'?type=video&id=8446',
        button: document.querySelector('#openVideo')
    },
    {
        mlink: link+'?type=image&id=81263',
        button: document.querySelector('#openGallery')
    },
    {
        mlink: link+'?type=bbs&id=2126282',
        button: document.querySelector('#openPoster')
    },
    {
        mlink: link+'?type=doublefloor&\
        id=aHR0cHM6Ly9iYnMuMzYwY2hlLmNvbS93ZWl4aW4vZG91YmxlZGVjay5waHA/cGlkPTIzMTQ3ODEyJnRpZD0yMTIyMzc2JnJlcGx5cGlkPTIzMTQ3ODEy&\
        title=%5B%E7%9B%B4%E6%92%AD%E5%B8%96%5D%E4%B8%80%E8%B5%B7%E5%8E%BB%E9%AB%98%E5%AE%89%E4%B9%B0%E8%BD%A6%EF%BC%8C%E5%8D%A1%E8%BD%A6%E4%B9%8B%E5%AE%B6%E5%85%A8%E7%A8%8B%E9%99%AA%E5%90%8C%E6%8B%85%E4%BF%9D',
        button: document.querySelector('#openFloor')
    }
];

new Mlink(options);
```

- options选项


```
{
    mlink: "短链KEY",
    button: document.querySelector('a#btnOpenApp'),     // 打开APP的a标签,必要参数并且只能是a标签
    autoLaunchApp : false,                              // 自动唤醒APP
    autoRedirectToDownloadUrl: true,                    // 打开APP失败重定项（到下载页）
    downloadWhenUniversalLinkFailed: false,
    inapp : false,
    params: {}                                          // 传给APP的参数
}
```



