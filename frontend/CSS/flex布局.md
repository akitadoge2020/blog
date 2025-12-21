---
sidebarDepth: 2
---

# flex布局

## 什么是flex布局？

Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。任何一个容器都可以指定为 Flex 布局，包括行级元素。

::: warning 注意
设为 flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效。
:::

```css
element {
    display: flex;
}
```

## 基本概念

采用 flex 布局的元素，称为 flex 容器（flex container），简称"容器"。它的直接子元素自动成为容器成员，称为 flex 项目（flex item），简称"项目"。

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做 main start，结束位置叫做 main end；交叉轴的开始位置叫做 cross start，结束位置叫做 cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做 main size，占据的交叉轴空间叫做 cross size。

![image-20250607154250731](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154250731.png)

## 容器的属性

### flex-direction

flex-direction 属性决定主轴的方向（即项目的排列方向）

接受以下取值：

`row(默认值)`：主轴方向从左到右

<img src="https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154736704.png" alt="image-20250607154736704"  />

`row-reverse`：主轴方向从右到左

![image-20250607154810013](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154810013.png)

`column`：主轴方向从上到下

<img src="https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154854976.png" alt="image-20250607154854976" style="zoom:50%;" />

`column-reverse`：主轴方向从下到上

<img src="https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154917260.png" alt="image-20250607154917260" style="zoom:50%;" />

### flex-wrap

flex-wrap 属性决定项目是否换行

接受以下取值：

`no-wrap(默认值)`：项目不换行，可能导致容器溢出（元素不压缩的情况下）

![image-20250607162455242](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607162455242.png)

`wrap`：项目换行

![image-20250607163800476](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607163800476.png)

`wrap-reverse`：和 `wrap` 行为一致，只是改变了交叉轴的方向

![image-20250607163825886](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607163825886.png)

::: warning 
这里你可能会好奇，为什么换行的项目没有紧跟着上一行，而是平分了容器的高度？答案在下面👇
:::



### justify-content

justify-content 属性定义了项目在**主轴**上的对齐方式

接受以下取值：

`flex-start(默认值)`：项目位于容器的开头

<img src="https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154736704.png" alt="image-20250607154736704"  />

`flex-end`：项目位于容器的结尾

![image-20250607154810013](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154810013.png)

`center`：项目位于容器的中央

![image-20250607164712435](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607164712435.png)

`space-between`：平分容器空间，首尾项目位于容器两侧

![image-20250607164731494](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607164731494.png)

`space-around`：平分容器空间，首尾项目与容器的距离，等于其他相邻容器距离的一半

![image-20250607164747899](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607164747899.png)

### align-items

align-items 属性定义项目在**交叉轴**上如何对齐

接收以下取值：

`flex-start`：项目位于容器的开头

<img src="https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154736704.png" alt="image-20250607154736704"  />

`flex-end`：项目位于容器的结尾

![image-20250607164844613](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607164844613.png)

`center`：项目位于容器的中央

![image-20250607164902073](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607164902073.png)

`baseline`：根据项目的第一行文字的基线对齐

![image-20250607170837628](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607170837628.png)

`stretch(默认值)`：如果项目没有定义高度或者 auto，将拉伸覆盖整个容器

![image-20250607171046182](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607171046182.png)



### align-content

align-content 属性定义了多行项目在交叉轴上的对齐方式。如果只有一行项目，该属性不起作用。

接收以下取值：

`flex-start`：项目位于容器的开头

![image-20250607215130577](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607215130577.png)

`flex-end`：项目位于容器的结尾

![image-20250607215149776](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607215149776.png)

`center`：项目位于容器中央

![image-20250607215213919](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607215213919.png)

`space-between`：平分容器空间，首尾项目位于容器两侧

![image-20250607215236007](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607215236007.png)

`space-around`：平分容器空间，首尾项目与容器的距离，等于其他相邻容器距离的一半

![image-20250607215259932](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607215259932.png)

`stretch`：如果项目没有定义高度或者 auto，将拉伸覆盖整个容器

![image-20250607163800476](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607163800476-20250607215408836.png)

::: details 为什么换行的项目不会紧跟在上一行后面，而是平分了容器高度？

这是因为 `align-content`属性的默认值`stretch`导致的，当项目设置了固定高度并且多行项目的高度合不足以占满容器时，它们将会平分剩余空间作为每行之间的间距。

:::



## 项目的属性

### order

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

```css
.item {
    order: 0;
}
```

### align-self

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性，但优先级没有align-content属性高。

接收以下取值：

`auto`

`flex-start`

`flex-end`

`center`

`baseline`

`stretch`

![image-20250607224521866](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607224521866.png)

### flex-grow

flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

```css
.item {
    flex-grow: 0;
}
```

<img src="https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607154736704.png" alt="image-20250607154736704"  />

```css
.item {
    flex-grow: 1;
}
```

![image-20250607224707360](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607224707360.png)

### flex-shrink

flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

```css
.item {
  /* 空间不足也不压缩项目 */
	flex-shrink: 0;
}
```

![image-20250607224757103](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607224757103.png)



根据上图所示，我们可以大概猜出压缩的公式是这样的，以下是建立在压缩比例相同的情况下：

8个元素总宽加起来超过容器的宽为100 * 8 - 600 = 200px，则每个元素需要压缩200 ÷ 8 = 25px，元素最终的宽为100 - 25 = 75px。

如果每个元素的宽度不同且压缩比例不同，又是如何压缩的呢？

```css
.item {
	flex-shrink: 1;
}

.item:nth-of-type(2) {
	width: 200px;
  flex-shrink: 2;
}

.item:nth-of-type(7) {
  width: 300px;
	flex-shrink: 3;
}
```

![image-20250607230815816](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250607230815816.png)

根据上图所示，计算压缩比例过程如下：

1. 先计算加权值，公式为：各个项目的宽度 * shrink值，即(100 * 1) * 6 + 200 * 2 + 300 * 3 = 1900px
2. 超出容器宽度：(100 * 6 + 200 + 300) - 600 = 500px
3. 然后计算每个项目需要压缩的宽度，公式为：每个元素所占权值的比例 * 超出容器的宽度
   1. 计算项目1、3、4、5、6、8需要压缩的宽度：（100 ÷ 1900）* 500 ≈ 26.3px
   2. 计算项目2需要压缩的宽度：（200 * 2 ÷ 1900）* 500 ≈ 105.3px
   3. 计算项目7需要压缩的宽度：（300 * 3 ÷ 1900）* 500 ≈ 236.9px
4. 最后得出项目压缩后的宽度分别为 73.7px、94.7px、63.1px

::: warning 注意
当每个项目变为 border-box，且有 border 或者 padding 时，元素的压缩会出现精度不准的问题。
:::

```css
.item {
	width: 100px;
  height: 100px;
  flex-shrink: 1;
  padding: 0 20px;
  box-sizing: border-box;
}

.wrapper > div:nth-of-type(2) {
  width: 200px;
  flex-shrink: 2;
  padding: 0;
}

.wrapper > div:nth-of-type(7) {
  width: 300px;
  flex-shrink: 3;
  padding: 0;
}
```

![image-20250615220407521](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250615220407521.png)

并且随着 border 或 padding 的增大，这个精度差也越来越大。当 border 或 padding 占满整个元素时，此时内容区宽高为0，可以发现，没设置 border 或 padding 的项目2和项目7已经被压缩为0了。

![image-20250615220840715](https://akitadoge-blog.oss-cn-guangzhou.aliyuncs.com/image-20250615220840715.png)

我们猜测，除了项目2、7，其余项目并没有参与到加权值的计算当中

由此推测出

**计算加权值的公式实际应为：各个元素的内容区宽度 * shrink值再相加**

现进行验证：

将所有项目的 padding 左右各设为10px，此时项目2内容区宽为180px，项目7的内容区宽为280px，其余项目的内容区宽度为80px，压缩比例为9 : 14 : 4，所有元素总宽超出容器200px

计算加权值： 40 * 1 + 40 * 1 + 240 * 3  =  800px

项目1、2需要压缩的宽度为： （40 * 1）/（800 * 200） =  10px

项目3需要压缩的宽度为： （240 * 3）/（800 * 200）=  180px

因此，经过压缩后，

项目1、2的现宽为： 200 - 10 = 190px

项目3的现宽为： 400 - 180 = 220px

验证成功！

![image-20220407165623036](https://penguinbucket.obs.cn-southwest-2.myhuaweicloud.com/img/image-20220407165623036.png)

### flex-basis

flex-basis属性定义了项目在容器中的初始宽度，默认为auto，即项目本身的宽度，也可以设置长度单位或百分比。

### flex

flex是以下属性的简写

- flex-grow
- flex-shrink
- flex-basis

```css
/* 默认值 */
flex: 0 1 auto;

/* 一个值, 无单位数字: flex-grow */
flex: 2;

/* 一个值, width/height: flex-basis */
flex: 10em;
flex: 30px;
flex: min-content;

/* 两个值: flex-grow | flex-basis */
flex: 1 30px;

/* 两个值: flex-grow | flex-shrink */
flex: 2 2;

/* 三个值: flex-grow | flex-shrink | flex-basis */
flex: 2 2 10%;
```

