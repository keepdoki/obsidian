## 全局
```
html,body {
  height: 95%;
  padding: 0.5em;
}
```
## 段落
```
p {
  text-align: justify;
  text-indent: 2em;
  duokan-text-indent: 2em;
  line-height: 130%;
  margin-top: 0.8em;
  margin-bottom: 0.8em;
  font-family: "宋体";
}

```

## 组合标题
```
<h2 class="Title-center"><span class="Title-num">第000章</span><br/><span class="Title-text">标题</span></h2>

.Title-center {
  font-family: "楷体";
  text-indent: 0;
  duokan-text-indent: 0;
  text-align: center;
  line-height: 130%;
  font-size: 1em;
  margin-top: 0.7em;
  margin-bottom: 1.2em;
  color: #972F34;
}
span.Title-num {
  font-family: "楷体";
  text-indent: 0;
  duokan-text-indent: 0;
  text-align: left;
  font-size: 0.7em;
  background-color: #d21f68;
  color: #fff;
  border-radius: 5px 5px 0 0;
  padding: 0.2em 0.3em 0.2em 0.3em;
}
span.Title-text {
  font-family: "yan";
  text-indent: 0;
  duokan-text-indent: 0;
  text-align: center;
  font-size: 1em;
  line-height: 130%;
  color: #972F34;
}

```


## 标题
```
.Title-center {
  font-family: "fzxbsf";
  text-indent: 0;
  duokan-text-indent: 0;
  text-align: center;
  line-height: 130%;
  font-size: 1em;
  margin-top: 0.7em;
  margin-bottom: 1.2em;
  color: #972F34;
}
```

## 双引号
```
span.talk {
  font-family: "细黑体", serif;
  color: #89001C;
}
```
## 单引号
```
span.emphasize {
  font-family: "楷体", serif;
  color: blue;
  // color: #228dcb;
}
```

## 头部图片
```
.Header-image-dk {
  text-align: right;
  text-indent: 0;
  duokan-text-indent: 0;
  margin: 0 0 0 0;
  margin-left: auto;
  page-break-before: always;
  duokan-bleed: lefttopright;
}
```