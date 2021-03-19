# mina-tool

![](https://track.yrobot.top/ga-beacon/UA-190592680-2/mina-tool/readme?flat)

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

_展示格式化：formatNumber, formatTime, formatCountdown_

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

<!-- 倒计时配合 `mina-countdown` 一起使用，更欢乐 -->
<!-- 00:01:02 -->
<view class="countdown">{{format.formatCountdown(62,'hh:mm:ss')}}</view>
<!-- 02:00 -->
<view class="countdown">{{format.formatCountdown(120,'mm:ss')}}</view>
...
```

[mina-countdown](https://github.com/Yrobot/mina-countdown)快速实现小程序倒计时
