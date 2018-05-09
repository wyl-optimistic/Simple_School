# css 那件小事

## 层叠次序
一般而言，所有的样式会根据下面的规则层叠于一个新的虚拟样式表中，其中数字 4 拥有最高的优先权。
1.  浏览器缺省设置
2.  外部样式表
3.  内部样式表（位于 <head> 标签内部）
4. 内联样式（在 HTML 元素内部）

## 值得不同写法和单位
除了英文单词 red，我们还可以使用十六进制的颜色值 #ff0000：
```
p { color: #ff0000; }
```
__为了节约字节，我们可以使用 CSS 的缩写形式：__对于rrggbb格式的颜色值可以用#rgb格式的简写表示.样式表会自动把不够6位的颜色值按 rgb=rrggbb的方式扩展成6位颜色值
```
p { color: #f00; }
```
我们还可以通过两种方法使用 RGB 值：
```
p { color: rgb(255,0,0); }
p { color: rgb(100%,0%,0%); }
```
__注意：__ 当使用 RGB 百分比时，即使当值为 0 时也要写百分比符号。但是在其他的情况下就不需要这么做了。比如说，当尺寸为 0 像素时，0 之后不需要使用 px 单位，因为 0 就是 0，无论单位是什么。

## 你应该知道的那些缩写
使用缩写可以减少CSS文件的大小，并且更加易于阅读。本文主要介绍CSS的主要缩写规则，内容涉及到颜色、盒尺寸、边框、背景、字体、列表等方面的内容。CSS缩写的主要规则如下：
* 颜色（见上例）
* 盒尺寸
>1.__property:value1__  -- 表示所有边都是一个值value1；<br>2.  __property:value1 value2__  -- 表示top和bottom的值是value1,right和left的值是value2<br> 3.  __property:value1 value2 value3__  -- 表示top的值是value1，right和left的值是value2，bottom的值是value3<br> 4.  __property:value1 value2 value3 value4__  --  四个值依次表示top,right,bottom,left (顺时针：上右下左)

* 边框（border）
语法：border:width style color;<br>
>__边框的属性如下：__<br>
border-width:1px; 　　border-style:solid; 　　border-color:#000;
__可以缩写为一句：__<br>
border:1px solid #000;

* 背景(Backgrounds)
 语法：background:color image repeat attachment position;<br>
 > __背景的属性如下：__<br>
 background-color:#f00; 　　background-image:url(background.gif); 　　background-repeat:no-repeat; 　　background-attachment:fixed; 　　background-position:0 0;<br>
__可以缩写为一句：__<br>
background:#f00 url(background.gif) no-repeat fixed 0 0;<br>
 __注意：__你可以省略其中一个或多个属性值，如果省略，该属性值将用浏览器默认值，默认值为:  __color: transparent 　　image: none 　　repeat: repeat 　　attachment: scroll 　　position: 0% 0%__
 
* 字体(fonts)
>__字体的属性如下：__<br>
font-style:italic; 　　font-variant:small-caps; 　　font-weight:bold; 　　font-size:1em; 　　line-height:140%; 　　font-family:"Lucida Grande",sans-serif;<br>
__可以缩写为一句：__<br>
font:italic small-caps bold 1em/140% "Lucida Grande",sans-serif;<br>
__注意：__ 如果你缩写字体定义，至少要定义font-size和font-family两个值。

* 列表(lists)
>__list的属性如下:__<br>
list-style-type:square; 　　list-style-position:inside; 　　list-style-image:url(image.gif);<br>
__可以缩写为一句：__<br>
list-style:square inside url(image.gif);<br>
__提示：__ 取消默认的圆点和序号可以这样写list-style:none;

## 记得写引号
__提示:__ 如果值为若干单词，则要给值加引号：
```
p {font-family: "sans serif";}
```

## CSS 属性选择器
 选择器        | 描述
-------------|----------------
 [attribute] | 用于选取带有指定属性的元素。
 [attribute=value]|	用于选取带有指定属性和值的元素。
 [attribute~=value]|用于选取属性值中包含指定词汇的元素。
 [attribute丨=value]|用于选取带有以指定值开头的属性值的元素，该值必须是整个单词。
 [attribute``^``=value]|匹配属性值以指定值开头的每个元素。
 [attribute$=value]|匹配属性值以指定值结尾的每个元素。
[attribute*=value]| 匹配属性值中包含指定值的每个元素。

## CSS背景
* 背景色

    可以为所有元素设置背景色，这包括 body 一直到 em 和 a 等行内元素。background-color __不能继承__，__其默认值是 transparent__。transparent 有“透明”之意。也就是说，如果一个元素没有指定背景色，那么背景就是透明的，这样其祖先元素的背景才能可见。
    
* 背景图片

    background-image 属性的默认值是 none，表示背景上没有放置任何图像。另外还要补充一点，background-image 也不能继承。__事实上，所有背景属性都不能继承。__

* 关键字

    图像放置关键字最容易理解，其作用如其名称所表明的。例如，top right 使图像放置在元素内边距区的右上角。根据规范，位置关键字可以按任何顺序出现，只要保证不超过两个关键字 - 一个对应水平方向，另一个对应垂直方向。如果只出现一个关键字，则认为另一个关键字是 center。
    
* 百分数值

    百分数值的表现方式更为复杂。假设你希望用百分数值将图像在其元素中居中，这很容易：（见下例）<br>
    这会导致图像适当放置，其中心与其元素的中心对齐。换句话说，百分数值同时应用于元素和图像。也就是说，图像中描述为 50% 50% 的点（中心点）与元素中描述为 50% 50% 的点（中心点）对齐。
    如果图像位于 0% 0%，其左上角将放在元素内边距区的左上角。如果图像位置是 100% 100%，会使图像的右下角放在右边距的右下角。
    如果只提供一个百分数值，所提供的这个值将用作水平值，垂直值将假设为 50%。这一点与关键字类似。
    background-position 的默认值是 0% 0%，在功能上相当于 top left。这就解释了背景图像为什么总是从元素内边距区的左上角开始平铺，除非您设置了不同的位置值。
```
body
  { 
        background-image:url('/i/eg_bg_03.gif');
        background-repeat:no-repeat;
        background-position:50% 50%;
  }
```

    
* 长度值

    长度值解释的是元素内边距区左上角的偏移。偏移点是图像的左上角。注意，这一点与百分数值不同，因为偏移只是从一个左上角到另一个左上角。也就是说，图像的左上角与 background-position 声明中的指定的点对齐。

* 背景关联

    如果文档比较长，那么当文档向下滚动时，背景图像也会随之滚动。当文档滚动到超过图像的位置时，图像就会消失。您可以通过 background-attachment 属性防止这种滚动。通过这个属性，可以声明图像相对于可视区是固定的（fixed），因此不会受到滚动的影响。__background-attachment 属性的默认值是 scroll__，也就是说，在默认的情况下，背景会随文档滚动。
    

## CSS文本
* 缩进文本（text-indent属性）

    通过使用 text-indent 属性，所有元素的第一行都可以缩进一个给定的长度，甚至该长度可以是负值。这个属性最常见的用途是将段落的首行缩进
    
    __注意__：一般来说，可以为所有块级元素应用 text-indent，但无法将该属性应用于行内元素，图像之类的替换元素上也无法应用 text-indent 属性。不过，如果一个块级元素（比如段落）的首行中有一个图像，它会随该行的其余文本移动。
   
    __提示：__如果想把一个行内元素的第一行“缩进”，可以用左内边距或外边距创造这种效果。
    >使用百分比
    text-indent 可以使用所有长度单位，包括百分比值。百分数要相对于缩进元素父元素的宽度。换句话说，如果将缩进值设置为 20%，所影响元素的第一行会缩进其父元素宽度的 20%。
    继承
    
* 水平对齐

    text-align 是一个基本的属性，它会影响一个元素中的文本行互相之间的对齐方式。__（注意：提示：将块级元素或表元素居中，要通过在这些元素上适当地设置左、右外边距来实现。）__
    - text-align:center 与 ``<CENTER>``
    
    您可能会认为 text-align:center 与 ``<CENTER> ``元素的作用一样，但实际上二者大不相同。``<CENTER> ``不仅影响文本，还会把整个元素居中。text-align 不会控制元素的对齐，而只影响内部内容。元素本身不会从一段移到另一端，只是其中的文本受影响。
    - justify
    
    在两端对齐文本中，文本行的左右两端都放在父元素的内边界上。然后，调整单词和字母间的间隔，使各行的长度恰好相等。您也许已经注意到了，两端对齐文本在打印领域很常见。是 CSS来确定两端对齐文本如何拉伸，以填满父元素左右边界之间的空间。
    需要注意的是，要由用户代理（而不是 CSS）来确定两端对齐文本如何拉伸，以填满父元素左右边界之间的空间
    
* 字间隔（word-spacing）

    word-spacing 属性可以改变字（单词）之间的标准间隔。其默认值 normal 与设置值为 0 是一样的。
    word-spacing 属性接受一个正长度值或负长度值。如果提供一个正长度值，那么字之间的间隔就会增加。为 word-spacing 设置一个负值，会把它拉近.
    
    ### ！！！word-spacing和letter-spacing的区别：
    
    __word-spacing是改变字和单词之间的间隔，判断的依据是两个字符之间是否有空格，连着的中文被认为是字符，word-spacing无效，应该用letter-spacing才会有效果。__
    

* 处理空白符（white-space 属性）

    值 | 空白符 | 换行符 | 自动换行
 ------ | ------ | ------- | ---------
 normal | 合并 | 忽略 | 允许
 pre-line | 合并 | 保留 | 允许
 nowrap | 合并 | 忽略 | 不允许
 pre | 保留 | 保留 | 不允许
 pre-wrap | 保留 | 保留 | 允许
注意：
值 pre：经测试，IE 7 以及更早版本的浏览器不支持该值；
值 pre-wrap 和 pre-line：在 IE7 和 FireFox2.0 浏览器中都没有得到很好的支持。
* 文本方向（direction属性）

    direction 属性影响 __块级元素__ 中文本的书写方向、表中列布局的方向、内容水平填充其元素框的方向、以及两端对齐元素中最后一行的位置。
    direction 属性有两个值： __ltr__ 和 __rtl__。大多数情况下，默认值是 ltr，显示从左到右的文本。如果显示从右到左的文本，应使用值 rtl。
    注：对于行内元素，只有当 unicode-bidi 属性设置为 embed 或 bidi-override 时才会应用 direction 属性。
    
## CSS字体
* 字体风格（font-style）
    
    该属性有三个值：

         normal - 文本正常显示
         italic - 文本斜体显示
         oblique - 文本倾斜显示

    ###  italic 和 oblique 的区别
    斜体（italic）是一种简单的字体风格，对每个字母的结构有一些小改动，来反映变化的外观。与此不同，倾斜（oblique）文本则是正常竖直文本的一个倾斜版本。通常情况下，italic 和 oblique 文本在 web 浏览器中看上去完全一样
    
* 字体加粗（font-weight）

    使用 bold 关键字可以将文本设置为粗体。
    
    关键字 100 ~ 900 为字体指定了 9 级加粗度。如果一个字体内置了这些加粗级别，那么这些数字就直接映射到预定义的级别，100 对应最细的字体变形，900 对应最粗的字体变形。数字 400 等价于 normal，而 700 等价于 bold。
    
## CSS链接
* 链接的样式

    链接的特殊性在于能够根据它们所处的状态来设置它们的样式。
    链接的四种状态：
    - a:link - 普通的、未被访问的链接
    - a:visited - 用户已访问的链接
    - a:hover - 鼠标指针位于链接的上方
    - a:active - 链接被点击的时刻
    
    __注意：__当为链接的不同状态设置样式时，请按照以下次序规则：
    - a:hover 必须位于 a:link 和 a:visited 之后
    - a:active 必须位于 a:hover 之后
    
## CSS列表
* 列表项图像（list-style-image）

    有时，常规的标志是不够的。你可能想对各标志使用一个图像，这可以利用 list-style-image 属性做到：
    ```
    ul li {list-style-image : url(xxx.gif)}
    ```
    
* 列表标志位置（ list-style-position）

    
    该属性用于声明列表标志相对于列表项内容的位置。外部 (outside) 标志会放在离列表项边框边界外，ul盒子内。内部 (inside) 标志处理为好像它们是插入在列表项内容最前面的行内元素一样，位于列表项边框内。
    
    值 | 描述
    ---- | -----
    inside | 列表项目标记放置在文本以内，且环绕文本根据标记对齐。
    outside |__默认值__。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不根据标记对齐。
    inherit | 规定应该从父元素继承 list-style-position 属性的值。
    
## css内边距
* 内边距的百分比数值

    可以为元素的内边距设置百分数值。百分数值是相对于其父元素的 width 计算的，这一点与外边距一样。所以，如果父元素的 width 改变，它们也会改变。
    
    __注意：__上下内边距与左右内边距一致；即上下内边距的百分数会相对于父元素宽度设置，而不是相对于高度。
    
## CSS 边框
* 边框与背景

    CSS 规范指出，边框绘制在__“元素的背景之上”__。这很重要，因为有些边框是“间断的”（例如，点线边框或虚线框），元素的背景应当出现在边框的可见部分之间。
CSS2 指出背景只延伸到内边距，而不是边框。后来__CSS2.1 进行了更正：元素的背景是内容、内边距和边框区的背景__大多数浏览器都遵循 CSS2.1 定义，不过一些较老的浏览器可能会有不同的表现。

* 边框的样式

    样式是边框最重要的一个方面，这不是因为样式控制着边框的显示（当然，样式确实控制着边框的显示），而是因为如果__没有样式，将根本没有边框。__

* 透明边框

    CSS2 引入了边框颜色值 transparent。这个值用于创建有宽度的不可见边框。

* 值复制

    CSS 定义了一些规则，允许为外边距指定少于 4 个值。规则如下：
    - 如果缺少左外边距的值，则使用右外边距的值。
    - 如果缺少下外边距的值，则使用上外边距的值。
    - 如果缺少右外边距的值，则使用上外边距的值。
    
## CSS 外边距合并
__外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。__
* 当一个元素出现在另一个元素上面时，第一个元素的下外边距与第二个元素的上外边距会发生合并。请看下图：
![](http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_1.gif '描述')
* 当一个元素包含在另一个元素中时（假设没有内边距或边框把外边距分隔开），它们的上和/或下外边距也会发生合并。请看下图：
![](http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_2.gif '描述')
* 假设有一个空元素，它有外边距，但是没有边框或填充。在这种情况下，上外边距与下外边距就碰到了一起，它们会发生合并：
![](http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_3.gif '描述')
* 如果这个外边距遇到另一个元素的外边距，它还会发生合并：

    ![](http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_4.gif '描述')
    
## 一切皆为框
div、h1 或 p 元素常常被称为块级元素。这意味着这些元素显示为一块内容，即“块框”。与之相反，span 和 strong 等元素称为“行内元素”，这是因为它们的内容显示在行中，即“行内框”。

__注意：__块级元素可以设置margin 和 padding.  行内元素的水平方向的padding-left,padding-right,margin-left,margin-right 都产生边距效果，但是竖直方向的padding-top,padding-bottom,margin-top,margin-bottom都不会产生边距效果。__（水平方向有效，竖直方向无效）__

在一种情况下，即使没有进行显式定义，也会创建块级元素。这种情况发生在把一些文本添加到一个块级元素（比如 div）的开头。即使没有把这些文本定义为段落，它也会被当作段落对待：
```
<div>
    some text
    <p>Some more text.</p>
</div>
```
在这种情况下，这个框称为无名块框，因为它不与专门定义的元素相关联。

__注意：__块级元素的文本行也会发生类似的情况。假设有一个包含三行文本的段落。每行文本形成一个无名框。无法直接对无名块或行框应用样式，因为没有可以应用样式的地方（注意，行框和行内框是两个概念）。但是，这有助于理解在屏幕上看到的所有东西都形成某种框。

## inline-block属性爬坑
问题描述：在类似
```
<div class="ovh">  
     <h3 class="lh24 h24">  
         <img class="dib"><p class="dib">学好css很重要</p>  
     </h3>      
</div>  
```
的布局中img和p都设置为inline-block。发现两个元素虽然在同一行上，但并不对齐。


是基线对齐问题，进一步来说，两个 inline-block 的元素都按照默认的垂直对齐方式为什么会产生不同的对齐效果？原因在于容器使用了 overflow: hidden 属性，这一属性改变了 inline-block 元素的基线位置，导致这一元素上移。因此，同时设置两个元素的垂直对齐方式为非基线对齐的值，或为另一个元素添加 overflow 属性都可以解决这一问题。

## CSS  position默认属性

#### static
元素框正常生成。块级元素生成一个矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中。

#### relative
元素框偏移某个距离。元素仍保持其未定位前的形状，它原本所占的空间仍保留。

相对定位是“相对于”元素在文档中的初始位置

#### absolute
元素框从文档流完全删除，并相对于其包含块定位。包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。

绝对定位的元素的位置相对于最近的已定位祖先元素，如果元素没有已定位的祖先元素，那么它的位置相对于最初的包含块。

#### fixed
元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身。

__提示：__相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。

## z-index属性爬坑
>z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。 
注释：元素可拥有负的 z-index 属性值。 
注释：Z-index 仅能在定位元素上奏效（position属性值设置除默认值static以外的元素，包括relative，absolute，fixed样式）

__注意!!!__ z-index无效的情况，一共有三种：
- 父标签 position属性为relative；
- 问题标签无position属性（不包括static）；
- 问题标签含有浮动(float)属性。

__解决办法：__
 - position:relative改为position:absolute；
 - 浮动元素添加position属性（如relative，absolute等）；
 - 去除浮动。
 
__z-index与其他CSS属性层叠上下文——非定位元素层叠上下文和z-index的关系__
![](../image/z-index.jpg '描述')

## css伪元素
属性 | 描述 | CSS定义版本
--------- | ---|------
: first-letter | 向文本的第一个字母添加特殊样式。 | 1
：first-line | 向文本的首行添加特殊格式。 |1
：before | 在元素之前添加内容 | 2
：after | 在元素之后添加内容 | 2
