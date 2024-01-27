1. 复制任意一件作为合集
	1. 确定通用样式`style.css`
	2. 删除非封面
	3. `OEBPS/content.opf`剔除无关信息
	4. 删除`Text`不相关文件
	5. `toc`删除不相关导航
	6. 打包zip.修改后缀成.epub
```
// OEBPS/toc.ncx
<navMap>
    <navPoint id="navPoint-1" playOrder="1">
      <navLabel>
        <text>封面</text>
      </navLabel>
      <content src="Text/cover.xhtml"/>
    </navPoint>
    <navPoint id="navPoint-2" playOrder="2">
      <navLabel>
        <text>制作信息</text>
      </navLabel>
      <content src="Text/message.xhtml"/>
    </navPoint>
</navMap>

// OEBPS/content.opf
<manifest>
    <item href="toc.ncx" id="ncx" media-type="application/x-dtbncx+xml" />
    <item href="Images/cover.jpg" id="cover.jpg" media-type="image/jpeg" />
    <item href="Text/cover.xhtml" id="cover.xhtml" media-type="application/xhtml+xml" />
    <item href="Text/message.xhtml" id="message.xhtml" media-type="application/xhtml+xml" />
  </manifest>
  <spine toc="ncx">
    <itemref idref="cover.xhtml" />
    <itemref idref="message.xhtml" />
  </spine>
```
2. 修改每个合集的文件夹 
	1. 在`Image`的文件名，加上`v001`(1是卷数)
	2. 搜索`src="../Images/`，替换成`src="../Images/v001`(1是卷数)
	3. 在合集的`toc.ncx`新建卷数，把对应卷数的`toc.ncx`剪切
	4. 打开`OEBPS/content.opf`，复制`spine`标签里面的`itemref`,修改`xhhtml`的文件名并生成`JSON`
	5. 按照生成的`JSON`修改导航和`toc.ncx`
	6. 打包成epub，**Sigil**软件打开，选择“**工具-目录-编辑目录**”，将重新生成的`id`和`playOrder`复制到`toc.ncx`