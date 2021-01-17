# mina-tool

小程序 开发实用工具集合  
主要包含几个维度：

1. 组件
2. behaviors
3. wxs
4. 样式

## 安装

1. `npm install mina-tool`
2. 微信开发者工具编译 npm 包

## 组件

### popup-window

_快速实现全屏浮动弹窗_
![](https://tva1.sinaimg.cn/large/0081Kckwly1gltjys368lj30u00lntak.jpg)

##### 体验

![](https://tva1.sinaimg.cn/large/0081Kckwly1glmk9m5e9jj3076076my2.jpg)

##### 使用

```json
{
  "usingComponents": {
    "popup-window": "mina-tool/components/popup-window"
  }
}
```

```html
<popup-window
  selector="{{selector}}"
  id="popup-window"
  tap-bg-close="{{true}}"
  catch-scroll="{{true}}"
  scroll-bg-close="{{true}}"
  visible="{{true}}"
  background-color="rgba(0,0,0,0.4)"
>
  <!-- popup-window内部展示slot -->
</popup-window>
```

### keyword-highlight

_快速支持关键词高亮，和原生 text 组件使用保持一致_
![](https://636f-could-test-1258393788.tcb.qcloud.la/README/screenshot-keyword-hightlight.jpeg)

##### 体验

##### 使用

```json
{
  "usingComponents": {
    "keyword-highlight": "mina-tool/components/keyword-highlight"
  }
}
```

```html
<keyword-highlight class="class" color="{{color}}" text="{{text}}" keyword="{{keyword}}" />
```

### multi-picker

_在小程序原生 picker - multiSelector 的基础上封装一层逻辑_  
feature：

1. 封装一层中间选择状态，保证选择过程中不会 trigger 外部状态变化
2. bindcancel 时自动将 picker 选择状态更新为外部状态，保证每次点开 picker 时的选中项和外部状态保持一致
3. 通过 getRanges，函数式更新 range 值，代码更简洁

##### 使用

```json
{
  "usingComponents": {
    "multi-picker": "mina-tool/components/multi-picker"
  }
}
```

```html
<multi-picker
  getRanges="{{getRanges}}"
  rangeKey="title"
  value="{{value}}"
  bindchange="{{onChange}}"
  bindcancel="{{onCancel}}"
>
  <!-- multi-picker内部展示slot -->
</multi-picker>
```

### error-img

_在 img 的 src 展示失败时，自动用 err 属性值更新 src 作为展示兜底_

##### 使用

```json
{
  "usingComponents": {
    "error-img": "mina-tool/components/error-img"
  }
}
```

```html
<error-img err="{{err_img_url}}" ...其他image属性 />
```

### data-status

_封装 数据请求展示过程中的一些状态展示：loading、empty、show_data_

##### 使用

```json
{
  "usingComponents": {
    "data-status": "mina-tool/components/data-status"
  }
}
```

```html
<data-status min-height="600rpx" loading="{{loading}}" empty="{{empty}}">
  <!-- data展示slot -->
</data-status>
```

## wxs

### format.wxs

_展示格式化：formatNumber, formatTime_

##### 使用

```html
<wxs src="mina-tool/wxs/format.wxs" module="format" />
...
<!-- 98.6万 -->
<view class="number">{{format.formatNumber(985800)}}</view>
<!-- 1.45亿 -->
<view class="number">{{format.formatNumber(145004545)}}</view>
<!-- 2021-01-04 -->
<view class="date">{{format.formatTime(1609756055278,'YYYY-MM-dd')}}</view>
...
```
