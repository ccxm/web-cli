## 全局样式

- 隐藏
```css
.g-hide {
    display: none;
}
```

- 显示
```css
.g-show {
    display: block;
}
```

- 禁用，禁止点击
```css
.g-disabled {
    pointer-events: none;
    cursor: default;
}
```

- 清除浮动
.g-clear-fix {
    &:after {
        content: ".";
        display: block;
        clear: both;
        /* height:0;和overflow:hidden;是为了解决IE兼容的问题 */
        height: 0;
        overflow: hidden;
        /* visibility:hidden;是为了去除content中的文字 */
        visibility: hidden;
    }
}

```css
.g-clear-fix {
    &:after {
        content: ".";
        display: block;
        clear: both;
        /* height:0;和overflow:hidden;是为了解决IE兼容的问题 */
        height: 0;
        overflow: hidden;
        /* visibility:hidden;是为了去除content中的文字 */
        visibility: hidden;
    }
}
```

- 遮罩层
```css
.g-mask {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4);
    z-index: 9999;
}
```

- 隐藏滚动条，适用于可以滚动但不需要滚动条的场景
```css
.g-hide-scroll {
    &::-webkit-scrollbar {
        display: none;
    }
}
```

- 背景图片，再定义一个background-image去覆盖
```css
.g-bg-img {
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center center;
}
```

## 全局样式

- 水平居中
```css
.x-center {
    display: flex;
    justify-content: center;
}
```

- 垂直居中
```css
.y-center {
    display: flex;
    align-items: center;
}
```

- 水平垂直居中
```css
.xy-center {
    display: flex;
    align-items: center;
    justify-content: center;
}
```

- 垂直水平居中并且纵向排列
```css
.yx-center {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
```

- 垂直排列并且两端对齐
```css
.y-center__between {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
```

- 垂直排列
```css
.y-flex {
    display: flex;
    flex-direction: column;
}
```

- 水平排列
```css
.x-flex {
    display: flex;
}
```

## 文本类样式

- 单行省略号，注意要加宽度，否则不生效
```css
.single-line-ellipsis {
    display: inline-block;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
```

- 多行省略号，行数自定义，引用时可以动态设置-webkit-line-clamp
```css
.multiple-line-ellipsis {
    overflow : hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
}
```

- 3行
```css
.multiple-line-ellipsis--3 {
    @extend .multiple-line-ellipsis;

    -webkit-line-clamp: 3;
}
```

- 4行
```css
.multiple-line-ellipsis--4 {
    @extend .multiple-line-ellipsis;

    -webkit-line-clamp: 4;
}
```

- 5行
```css
.multiple-line-ellipsis--5 {
    @extend .multiple-line-ellipsis;

    -webkit-line-clamp: 5;
}
```

## 三角形
- 垂直方向的三角形
```css
.g-triangle-vertical{
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
}
```

- 水平方向的三角形
```css
.g-triangle-horizontal {
    width: 0;
    height: 0;
    border-top: 5px solid transparent;
    border-bottom: 5px solid transparent;
}
```
- 向上
```css
.g-triangle-top {
    @extend .g-triangle-vertical;

    border-bottom: 5px solid #333;
}
```

- 向下
```css
.g-triangle-bottom {
    @extend .g-triangle-vertical;

    border-top: 5px solid #333;
}
```

- 向左
```css
.g-triangle-left {
    @extend .g-triangle-horizontal;

    border-right: 5px solid #333;
}
```

- 向右
```css
.g-triangle-right {
    @extend .g-triangle-horizontal;

    border-left: 5px solid #333;
}
```

## 全局mixin
- 设置背景图片
```css
@mixin set-bg-img($url) {
    @extend .g-bg-img;

    background-image: url($url);
}
```

- 多行文本超出显示省略号
```css
@mixin multiple-ellipsis($width: 100%, $display: block, $line: 2) {
    width: $width;
    display: $display;
    -webkit-line-clamp: $line;
    overflow : hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
}
```

- 自定义三角形，bottom: 底，size: 边，dir：方向
```css
@mixin create-triangle($bottom: 5px, $size: 6px, $dir: 'top', $color: #333) {
    $border-size: $bottom solid $color;
    $transparent-size: $size solid transparent;

    width: 0;
    height: 0;
    @if ($dir == 'top' or $dir == 'bottom') {
        width: 0;
        height: 0;
        border-left: $transparent-size;
        border-right: $transparent-size;

      @if ($dir == 'top') {
          border-bottom: $border-size;
      }

      @if ($dir == 'bottom') {
          border-top: $border-size;
      }
    }

    @if ($dir == 'left' or $dir == 'right') {
      width: 0;
      height: 0;
      border-bottom: $transparent-size;
      border-top: $transparent-size;

      @if ($dir == 'left') {
          border-right: $border-size;
      }

      @if ($dir == 'right') {
          border-left: $border-size;
      }
    }
}
```

## 全局函数
待更新~

## 下载地址
[点击下载](https://github.com/ccxm/web-cli/tree/master/css)
