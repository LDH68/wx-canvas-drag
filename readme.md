## Tip：修改于 wxa-comp-canvas-drag

## wx-canvas-drag

小程序组件-canvas 拖拽画板

## 概述

wx-canvas-drag 是一个可以添加多种元素（图片和文字）的画板，用户可以移动拖拽元素组成自己喜欢的样子并导出图片。

## 组件效果


![图片信息描述](https://github.com/LDH68/image/blob/main/gif/wx-canvas-drag.gif)


## 使用之前

使用前，请确保你已经学习过微信官方的 [小程序简易教程](https://mp.weixin.qq.com/debug/wxadoc/dev/) 和 [自定义组件介绍](https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/)。

## 安装

直接通过 git 下载 wx-canvas-drag 源代码，并将`miniprogram_dist`目录拷贝到自己的项目组件目录中

## 使用组件

```json
{
  "usingComponents": {
    "canvas-drag": "/components/canvas-drag/index"
  }
}
```

接着就可以在 wxml 中插入组件

```html
<canvas-drag
  id="canvas-drag"
  graph="{{graph}}"
  width="700"
  height="750"
></canvas-drag>
```

## 组件参数解释

| 字段       | 类型    | 必填             | 描述                         |
| ---------- | ------- | ---------------- | ---------------------------- |
| graph      | Object  | 否               | 看下文                       |
| bgColor    | String  | 否               | 画板背景颜色                 |
| bgImage    | String  | 否               | 画板背景图片地址（本地地址） |
| width      | Number  | 否（默认 750）   | 画板宽度（单位 rpx）         |
| height     | Number  | 否（默认 750）   | 画板高度（单位 rpx）         |
| enableUndo | Boolean | 否（默认 false） | 是否启用后退                 |

### graph 字段

| 字段     | 类型                        | 必填                    | 描述                                          |
| -------- | --------------------------- | ----------------------- | --------------------------------------------- |
| type     | String（'text'或者'image'） | 是                      | 加入画板的元素类型，有 text 和 image 两种类型 |
| w        | Number                      | type=image 时，必填     | 图片宽度                                      |
| h        | Number                      | type=image 时，必填     | 图片高度                                      |
| url      | String                      | type=image 时，必填     | 图片地址（本地地址）                          |
| sourceId | String                      | type=image 时可用，选填 | 图片信息（导出模板用）                        |
| text     | String                      | type=text 时，必填      | 文本内容                                      |

## 对外暴露接口

组件通过 canvas-drag.js 对外暴露了以下几个接口

| 接口名         | 入参                                 | 返回                                 | 描述                       |
| -------------- | ------------------------------------ | ------------------------------------ | -------------------------- |
| export         | 无                                   | Promise 对象，成功回调返回图片地址   | 导出画板生成的图片地址     |
| exportJSON     | 无                                   | Promise 对象，成功回调返当前画板配置 | 导出画板布局数据           |
| clearCanvas    | 无                                   | 无                                   | 清空画布                   |
| initByArr      | exportJSON 导出的数据                | 无                                   | 用配置文件一次渲染多个元素 |
| changFontColor | color（改变的颜色值）                | 无                                   | 改变选择文本颜色           |
| changeBgColor  | color（改变的颜色值）                | 无                                   | 改变画板背景颜色           |
| changeBgImage  | imageUrl（图片地址（本地地址））     | 无                                   | 改变画板背景图片           |
| changeBgImage  | {url:"图片 URL",sourceId:"图片信息"} | 无                                   | 改变画板背景图片           |
| undo           | 无                                   | 无                                   | 回到上一次的状态           |

## 问题反馈

有什么问题可以直接提 issue
