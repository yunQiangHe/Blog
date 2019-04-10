---
title: Lodop使用说明
date: 2019-04-09 09:39:36
categories:
tags:
description: table表格 td设置固定宽度
---

[Wingdings 符号编码对照表])(https://blog.csdn.net/Linux7985/article/details/5030694)

table宽度自适应，而且部分TD是固定宽度。

只需要将固定宽设死，留下一列不设置宽度，将table宽度设置为100%。

```
table-layout:fixed 作用不是很清楚

<table width="100%" border="1" cellpadding="0" cellspacing="0" style="table-layout:fixed">
  <tr>
    <td width="50">10</td>
    <td width="50">20</td>
    <td width="50">30</td>
    <td width="50">40</td>
    <td width="100">50</td>
    <td> </td>
  </tr>
  <tr>
    <td>宽度50</td>
    <td>宽度多多余</td>
    <td>宽度多余100想要换行</td>
    <td> </td>
    <td> </td>
    <td> </td>
  </tr>
  <tr>
    <td> </td>
    <td> </td>
    <td> </td>
    <td> </td>
    <td> </td>
    <td> </td>
  </tr>
</table>
```

```
●	PRINT_INIT(strPrintTaskName)打印初始化
●	SET_PRINT_PAGESIZE(intOrient,intPageWidth,intPageHeight,strPageName)设定纸张大小
●	ADD_PRINT_HTM(intTop,intLeft,intWidth,intHeight,strHtml)增加超文本项
●	ADD_PRINT_TEXT(intTop,intLeft,intWidth,intHeight,strContent)增加纯文本项
●	ADD_PRINT_TABLE(intTop,intLeft,intWidth,intHeight,strHtml)增加表格项
●	ADD_PRINT_SHAPE(intShapeType,intTop,intLeft,intWidth,intHeight,intLineStyle,intLineWidth,intColor)画图形
●	SET_PRINT_STYLE(strStyleName, varStyleValue)设置对象风格
●	PREVIEW打印预览
●	PRINT直接打印
●	PRINT_SETUP打印维护
●	PRINT_DESIGN打印设计
```