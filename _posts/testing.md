
# <center>利用 Python 进行数据可视化</center> 
---
<p align="right">东南大学-经济管理学院-GS119530-薛皓元</p>

## 引言

此文档首先是作为在东南大学大一的通选课 Python 语言与数据科学的期末大作业而写的，因为平生首次接触文档的书写和 GitPages 的配置，很多地方都多有不妥，希望老师谅解！感谢夏老师在本学期的教学，能选到夏老师的课真的是非常幸运，如果有机会，以后我也会选择旁听夏老师的其他课的！

再说说个人认为的数据可视化，个人认为数据可视化是旨在借助于图形化手段，清晰有效地传达与沟通信息，是指将大型数据集中的数据以图形图像形式表示，并利用数据分析和开发工具发现其中未知信息的处理过程。

其次，数据可视化并不是简单的把数据变成图表。而是以数据为视角，看待世界。换句话说，数据可视化的客体是数据，但我们想要的其实是——数据视觉，以数据为工具，以可视化为手段，目的是描述真实，探索世界。

本文档将会以 Python 相关工具为主视角，尽可能多的阐述数据可视化的相关工具及其描述方法。注：本文档使用的非 random 数据或数据集将附在文末连接处。

## 0 序言
### -数据可视化简介

**数据可视化（Data Visualization）**，利用人对形状、颜色的感官敏感，来研究如何利用图形来展现数据中隐含的信息，挖掘数据中包含的关系、规律、趋势。

常用基础图表有**饼图、散点图、折线图、柱形图、雷达图**等，操作时根据数据间的关系，选择相应合适的图表。

>**成分**：用来表示部分和总体的关系，一般用饼图表示。如果类别较少，可以用圆环图，如果类别较多，可以用树状图来展示。

>**排序**：展示不同的数值大小，常用柱形图、条形图、气泡图来展示。

>**时间序列**：如果只有一个序列，可用折线图、柱状图来展示；如果多个序列，首选折线图。

>**频率分布**：和排序类似，但通常展示的是分组。

>**相关性**：通常用散点图表示，也可以使用分组柱形图、旋风图、气泡图等

>**多重数据比较**：对多个维度的数据进行展示，一般使用雷达图。

![TP.jpg](https://vip1.loli.net/2020/06/15/oebfN6zkWPQplUx.jpg)

### -数据可视化的意义

数据可视化的作用：表达形象化、重点突出化、体现专业性。

数据可视化的主要作用，在于通过图形和色彩将关键数据和特征直观地传达出来，从而实现对于相当稀疏而又复杂的数据集的深入洞察。单纯说“呈现”，并不确切，因为数据可视化并非无差异地涵盖所有数据，可视化的过程本身就已经加入了制作人的对问题的思考、理解、甚至是一些假设，而数据可视化则是通过一目了然地方式，帮助制作人获得客观数据层面的引导或者验证。

* 1、传递速度快人脑对视觉信息的处理要比书面信息块10倍。使用图表来总结复杂的数据，可以确保对关系的理解要比那些混乱的报告或电子表格更快。
* 2、数据显示的多维性在可视化的分析下，数据将每一维的值分类、排序、组合和显示，这样就可以看到表示对象或事件的数据的多个属性或变量。
* 3、更直观的展示信息大数据可视化报告使我们能够用一些简短的图形就能体现那些复杂信息，甚至单个图形也能做到。决策者可以轻松地解释各种不同的数据源。丰富但有意义的图形有助于让忙碌的主管和业务伙伴了解问题和未决的计划。
* 4、大脑记忆能力的限制在观察物体的时候，人类的大脑和计算机一样有长期的记忆(memory 硬盘)和短期的记忆(cache 内存)的区分。只有我们让要记下文字，诗歌，物体，一遍一遍的在短期记忆里不断重复出现之后, 它们才可能进入长期记忆。

Python数据可视化的基本工具有matplotlib、Bokeh和pyechart等,下面部分文段会对这几种工具进行详述。

## 1 **数据可视化 -- matplotlib 篇**

### -关于 matplotlib 库的简介

matplotlib 是 python 最著名的2D绘图库，可以称之为 Python 数据可视化库的泰斗，已经有十多年的历史，它提供了一整套和matlab相似的命令API，与 MATLAB 非常相似，十分适合交互式地进行制图。而且也可以方便地将它作为绘图控件，嵌入GUI应用程序中。通过简单的绘图语句，就可以绘制出高质量的图了。

通过 Matplotlib，开发者可以仅需要几行代码，便可以生成绘图，直方图，功率谱，条形图，错误图，散点图等。

### 1.1 简明 matplotlib API 入门

![图表.png](https://vip1.loli.net/2020/06/15/vwgIBlOa71VPxcq.png)

#### 1.1.1 简单线性图的绘制及保存
在使用 matplotlib 时，一般使用以下的导入惯例：

```python
 import matplotlib.pyplot as plt
```
下面尝试生成一个简单的图形/线性图，并将其保存。

```python
import matplotlib.pyplot as plt
import numpy as np

data = np.arange(10)
plt.plot(data)
plt.savefig('matplotlib1.jpg')
```
具体生成图形如下图所示：

![matplotlib1.jpg](https://vip1.loli.net/2020/06/15/2MWH9sDZQudi4tb.jpg)

其中,你可以使用 plt.savefig 将图片保存至文件，savefig 的相关参数选项如下：
参数|描述
--|:--:
fname|包含文件路径或 Python 文件型对象的字符串；其中，图片格式是从文件扩展名中推断出来的
dpi|每英寸点数的分辨率；默认是100，可编辑配置
dacecolor,edgecolor|子图之外的图形背景颜色；默认为'w'，即白色
format|文件格式，如：png pdf jpg eps svg 等
bbox_inches|要保存的图片范围；如传递'tight'，将会去除图片周围的空白部分

所以，根据上述参数及描述，如果希望的到一个简洁的，文件格式为 png 格式，分辨率为 300 DPI 的相同图形，需要运行以下代码：

```python
plt.savefig('matplotlib1.png', dpi = 300, bbox_inches = 'tight')
```

当然，可视化过程中所处理的数据一般是更加多维，更加复杂的，一张图标往往不足以呈现多元的数据，所以图表中的子图就相当重要。

#### 1.1.2 图片与子图

matplotlib 所绘制的图片位于图片（ Figure ) 对象中，一般可以使用 plt.figure 生成一个全新的图片，该空白图片不能直接对象绘图，进而需要使用 add_subplot 创建一个或者多个子图,输入以下代码，会得到图片如下所示：

```python
import matplotlib.pyplot as plt
import numpy as np

fig = plt.figure()
ax1 = fig.add_subplot(2, 2, 1)
ax2 = fig.add_subplot(2, 2, 2)
ax3 = fig.add_subplot(2, 2, 3)

plt.plot([1.5, 3.5 -2, 1.6])
plt.plot(np.random.randn(50).cumsum(), 'k--')
plt.savefig('matplotlib2.jpg')
```

![matplotlib2.jpg](https://vip1.loli.net/2020/06/15/bsoAFNkWwVMcdmY.jpg)

其中，'k--' 是用于绘制黑色分段线的 style 选项，后面部分会介绍。

fig.add_subplot 返回的对象是 Axes Subplot 对象，使用这些对象可以直接在其他空白子图上调用对象进行绘图。

```python
_ = ax1.hist(np.random.randn(100), bins = 20, color = 'k', alpha = 0.3)
ax2.scatter(np.arange(30), np.arange(30) + 3 * np.random.randn(30))
```

![matplotlib3.jpg](https://vip1.loli.net/2020/06/15/BRKyht18L4EZfTc.jpg)

同样的，数组 axes 也可以像二维数组一样使用索引，如： axes[0,1]

pyplot.subplots 相关选项如下表所示：

参数|描述
--|:--:
nrows|子图的行数
ncols|子图的列数
sharex|所有子图使用相同的x轴刻度，调整 xlim 会影响所有子图
sharey|所有子图使用相同的y轴刻度，同上
subplot_kw|传入 add_suplot 的关键字参数字典，用于生成子图
**fig_kw|在生成图片时使用的额外关键字参数

同时，在绘制图片时，可以使用图对象上的 subplots_adjust 更改间距,例：

```python
subplots_adjust(left = None, bottom = None, right = None, top = None, hspace = None)
```

wspace 和 hspace 分别控制图片的宽度和高度百分比，调整图片的宽度和高度百分比可以用作调整子图之间的间距，在此不举例。

除了图片和子图，matplotlib 还可以进行更多的个性化设置，以让图片具有更强的可看性。

#### 1.1.3 颜色、标记和线类型

matplotlib 的主函数 plot 接受带有x和y轴的数组以及一些可选的字符串缩写参数来指明颜色和线类型，例如：

```python 
import matplotlib.pyplot as plt
import numpy as np

data = np.random.randn(30).cumsum()
plt.plot(data, 'k--', label = 'Default')
plt.plot(data, 'k-', drawstyle = 'steps-post', label = 'steps-post')
plt.savefig('matplotlib4.jpg')
```

![matplotlib4.jpg](https://vip1.loli.net/2020/06/15/ersazjtGkKO43AT.jpg)

由此，我们可以在不同 drawstyle 选项下做出不同效果的线条来满足更加个性化的需求，从而让图片更加完善和清晰，同样可利用不同控制符，个性化我们的线条：

字符|颜色|字符|类型
--|:--:|:--:|:--:
'b'|blue|'-'|实线
'g'|green|'--'|虚线
'r'|red|'-.'|虚点线
'c'|cyan 青色|':'|点线
'm'|magenta平红|' '|空类型，不显示线
'y'|yellow
'k'|black
'w'|white

另有点类控制符如下图：

![图片源自网络.jpg](https://vip1.loli.net/2020/06/15/Jaqh9GzkPQX2Kmd.jpg)

#### 1.1.4 刻度、标签和图例

如果图片中出现多个不容易分清的线条，还可以通过 plt.legend 为每条线生成一个用于区分的图例。

通过 set_title 可以为图片设置标题，通过 set_xlabel 和 set_xticklabels 可以变更图片的X轴坐标,同理可以类比y轴坐标，在此不做赘述。

加上以下代码，可以得到后图。

```python 
plt.legend(loc = 'best')
ticks = ax.set_yticks([0, 5, 10, 20, 30])
labels = ax.set_xticklabels(['one', 'two', 'three', 'four', 'five'])
ax.set_title('Title Testing')
ax.set_xlabel('stages')
```

![matplotlib5.jpg](https://vip1.loli.net/2020/06/15/GByQFJdjeN9ZMCL.jpg)

当然，我们也可以根据之前的设置统一对图例等参数进行修改：

```python
props = {
    'title': 'Title Testing'
    'xlabel'： 'stages'
}
ax.set(**props)
```

#### 1.1.5 注释与子图加工

除了标准的绘图，绘图时可能还需要在图表上绘制自己的注释，对于包含文本、箭头以及其他图形的注释，可以通过使用 text 、 arrow 和 annote 来添加注释和文本。

另外，也可以通过 Rectangle 和 Circle 等绘制常见图形,如：

```python
fig = plt.figure(figsize=(12, 6)); ax = fig.add_subplot(1, 1, 1)
rect = plt.Rectangle((0.2, 0.75), 0.4, 0.15, color = 'k', alpha = 0.3)
circ = plt.Circle((0.7, 0.2), 0.15, color = 'b', alpha = 0.3)
pgon = plt.Polygon([[0.15, 0.15], [0.35, 0.4], [0.2, 0.6]], color = 'g', alpha = 0.5)

ax.add_patch(rect)
ax.add_patch(circ)
ax.add_patch(pgon)
```

最后，还可以使用个 rc 对 matplotlib 的设置进行更改，如：
```python
plt.rc('figure', figsize=(10, 10))

font_options = {'family': 'monospace', 'weight' : 'bold', 'size' : 'small'}
plt.rc('font', **font_options)
```

下面，将会就具体图形的绘制展开说明。

### 1.2 折线图

折线图的核心思想是**趋势变化**，作为信息最明了的图表，它也是各种图表中最容易解读的图表。

* 折线图是点、线连在一起的图表，可反映事物的发展趋势和分布情况；

* 适合在单个数据点不那么重要的情况下表现变化趋势、增长幅度。

绘制折线图通常会用到 plot 工具用来绘制，而 plt.plot 的本质，实际上就是根据点连城线，也就是根据数组和列表中的x和y坐标做出点，然后将点连成线， plot 工具默认是绘制折线图的。

```python
import matplotlib.pyplot as plt

x = ['3/11', '3/12', '3/13', '3/14']
y = [4, 1, 3, 2]

fig = plt.figure()
plt.plot(x, y)
plt.savefig('matplotlib7.jpg')
```
![matplotlib7.jpg](https://vip1.loli.net/2020/06/16/CpcWq67vjA8OUny.jpg)

同样，可以利用同一个X轴坐标下的不同y轴值在同一个图表上绘制多个折线图，可另外自由实践。

plot函数的部分参数如下表所示：

参数|描述
--|:--:
label|图例/标签
ax|绘图使用的自图对象，如没有传值则默认当前编辑的子图
style|窜给 matplotlib 的样式字符串，如：'ko--'
alpha|图片不透明度，从0到1
kind|可以是'area'/'bar'/'hist'/'kde'/'line' 等
logy|在y轴上使用对数缩放
use_index|使用对象索引刻度标签
rot|刻度标签的旋转，从0到360
xtick/ytick|用于x/y轴刻度的值
xlim/ylim|x/y轴的范围
grid|展示轴网络，默认打开

另： Series 和 DataFrame 都有一个 plot 属性，可以用于绘制基本图形。

### 1.3 柱状图/条形图

柱形图的核心思想是**对比**，是以宽度相等的条形高度或长度的差异来显示统计指标数值多少或大小的一种图形。柱形图简明、醒目，是一种常用的统计图形。 

柱形图用于显示一段时间内的数据变化或显示各项之间的比较情况。类似的图形表达为直方图，不过后者较柱状图而言更复杂(直方图可以表达两个不同的变量)，此外，相似的还有扇形统计图和折线统计图。

1) 核心是对比，柱形图的目的是将对比信息放大，直观呈现出来；

2) 由于直观，柱形图适合做结论的表达；

3) 柱形图一般不用在时间维度的变化；

4) 柱形图的数据系列和点不宜过多，否则建议改变图表形式；

5) 柱形之间的宽度尽量小于柱形本身的宽度。

柱形图一般使用 bar 或 barh 工具,其中 barh 为以y轴为刻度的柱形图，bar 函数的相关参数如下表：

参数|说明|类型
--|:--:|:--:
x|x坐标|int,float
height|条形的高度|int,float
width|宽度|0~1，默认0.8
botton|条形的起始位置|也是y轴的起始坐标
align|条形的中心位置|“center”,"lege"边缘
color|条形的颜色|“r","b","g","#123465"，默认“b"
edgecolor|边框的颜色|同上
linewidth|边框的宽度|像素，默认无，int
tick_label|下标的标签|可以是元组类型的字符组合
log|y轴使用科学计算法表示|bool
orientation|是竖直条还是水平条|竖直："vertical"，水平条："horizontal"

简单柱形图如下图。

```python
import matplotlib.pyplot as plt

x = ['3/11', '3/12', '3/13', '3/14']
y = [4, 1, 3, 2]

fig = plt.figure()
plt.bar(x, y)
plt.savefig('matplotlib8.jpg')
```

![matplotlib8.jpg](https://vip1.loli.net/2020/06/16/DsELP8COnUQb9JR.jpg)

### 1.4 饼图

饼图的核心思想是**分解**，饼图显示一个数据系列中各项的大小与各项总和的比例。饼图中的数据点显示为整个饼图的百分比。
* 一般来说，数值最大的部分排在最前面，也就是12点钟方向顺时针；

* 饼图的细分项不宜过多，一般不超过8项；

* 不要制作三维的饼图，不直观；

* 切忌将饼图拉得过开，若要突出某一块，可单独将其拉开。

运用 pie 函数绘制简单饼图，注意，此处 labels 为数值标签数组，即对饼图的每块扇形的标记。

参数|说明
--|:--:
x|输入的数据用于创建一个饼图。
explode|默认为None。如果不是None，是一个长度与x相同长度的数组，用来指定每部分的偏移量。
labels|默认为：None。一个字符串序列作为每个饼块的标记。
colors|默认为：None。用来标注每块饼图的matplotlib颜色参数序列。如果为None，将使用当前活动环的颜色。
autopct|默认是None。如果不是None，是一个字符串或函数用带有数值饼图标注。                
pctdistance|默认值：0.6。每个饼切片的中心和通autopct生成的文本开始之间的比例。如果autopct是None，被忽略。
shadow|默认值：False。在饼图下面画一个阴影。
labeldistance|默认值：1.1。被画饼标记的直径。
startangle|默认：None。如果不是None，从x轴逆时针旋转饼图的开始角度。
radius|默认为：None。饼图的半径，如果半径是None，将被设置成1。
counterclock|默认为：None。指定指针方向，顺时针或者逆时针。
textprops|默认值为：None。传递给text对象的字典参数。
center|默认值：(0,0)。图标中心位置。
frame|默认值：False。如果是true，绘制带有表的轴框架。
rotatelabels|默认为：False。如果为True，旋转每个label到指定的角度。

```python
import matplotlib.pyplot as plt

x = ['3/11', '3/12', '3/13', '3/14']
y = [4, 1, 3, 2]

fig = plt.figure()
plt.pie(y, labels=x)
plt.savefig('matplotlib9.jpg')
```

![matplotlib9.jpg](https://vip1.loli.net/2020/06/16/6DaIyFBcUZsPinf.jpg)

其实，个人觉得饼图在实际场景中应当尽可能少的使用(因人眼对面积大小不敏感），而且对指标的分解柱形图同样能胜任，且远远清晰于饼图；当且仅当，用于反应单个模块占整体比重时，适合用饼图。

### 1.5 散点图和点图

散点图的核心思想是**研究**，它是用于观测数据的相关性的，有正相关，负相关，不相关，是典型的研究型图表，适合用于发现变量间的关系与规律，但是不适合用于清晰表达信息的场景。

绘制散点图会用到 scatter 工具，下面是一个简单的随机点图。

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.random.normal(0, 1, 99)
y = np.random.normal(0, 1, 99)
z = np.random.normal(0, 1, 99)

fig = plt.figure()
plt.scatter(x, y, s=111, alpha=0.4)
plt.savefig('matplotlib10.jpg')
```

![matplotlib10.jpg](https://vip1.loli.net/2020/06/16/PI5ZV3lDGNUA71u.jpg)

其中，x/y 是点的横纵坐标，s 是点的面积，alpha 是点的透明度，另外，还可以设置 ‘c’ 为点的颜色，‘ marker’ 是点的形状等。

还可以通过 seaborn 的 regplot 方法，该方法可以绘制出散点图，并拟合出一条线性回归线，可以自主尝试。

* 散点图作为研究型图表，经常在数据分析前期被使用，在报告中很少见；

* 散点图不够直观，大多时候不能直接表达结论；

* 散点图对于业务敏感度和数据意识要求较高；

* 散点图只是入门的钥匙，发现规律只是分析的切入口。

#### -三维散点图

三维散点图相较于二维散点图而言所用函数参数没有太大差别，但是 mplot3D 能让图表在描述多维度关系中更加清晰明确。

```python
import matplotlib.pyplot as plt
import numpy as np
from mpl_toolkits import mplot3d

x = np.random.normal(0, 1, 99)
y = np.random.normal(0, 1, 99)
z = np.random.normal(0, 1, 99)

fig = plt.figure()
ax = mplot3d.Axes3D(fig)
ax.scatter(x, y, z, s=111, alpha=0.3)
plt.savefig('matplotlib11.jpg')
```

![matplotlib11.jpg](https://vip1.loli.net/2020/06/16/tlyVBg5xuNSQCTW.jpg)



### 1.6 热力图

热力图是以特殊高亮的形式显示访客热衷的页面区域和访客所在的地理区域的图示。多用于统计用户或个体行为，功能具备大多数的流量统计软件不具备的优势，即，通过色差、亮度来展示数据的差异、易于理解。

plt.imshow 不同于 plt.show 是用于绘制热力图的 matplotlib 工具，

参数|说明
--|:--:
x|图像数据
cmap|将标量数据映射到色彩图
aspect|控制轴的纵横比。该参数可能使图像失真，即像素不是方形的
alpha|alpha值，介于0（透明）和1（不透明）之间
extent|数据坐标中左下角和右上角的位置

```python
import matplotlib.pyplot as plt
import numpy as np

a = np.linspace(-3, 3, 999)
x, y = np.meshgrid(a, a)
z = (1 - x / 2 + x ** 5 + y ** 3) * np.exp(-x ** 2 - y ** 2)

fig = plt.figure()
plt.imshow(z, origin='low', cmap='jet')
plt.colorbar()
plt.savefig('matplotlib12.jpg')
```

![matplotlib12.jpg](https://vip1.loli.net/2020/06/16/6rFU2CilzRkGmNP.jpg)

### 1.7 等高线图

contour 和 contourf 都是画三维等高线图的，不同点在于contourf会对等高线间的区域进行填充,运用简单数据绘制等高线图。

```python
import matplotlib.pyplot as plt
import numpy as np
from mpl_toolkits import mplot3d

a = np.linspace(-3, 3, 999)
x, y = np.meshgrid(a, a)
z = (1 - x / 2 + x ** 5 + y ** 3) * np.exp(-x ** 2 - y ** 2)

fig = plt.figure()
cntr = plt.contour(x, y, z, colors='black')
plt.contourf(x, y, z, cmap='jet')
plt.clabel(cntr, fmt='%.1f')
plt.colorbar()
plt.savefig('matplotlib13.jpg')
```

![matplotlib13.jpg](https://vip1.loli.net/2020/06/16/qWDVrLCJISgQhbn.jpg)

### 1.8 三维热力图

类似热力图，虽然小众但是依旧非常直观简明。

```python
import matplotlib.pyplot as plt
import numpy as np
from mpl_toolkits import mplot3d

a = np.linspace(-3, 3, 999)
x, y = np.meshgrid(a, a)
z = (1 - x / 2 + x ** 5 + y ** 3) * np.exp(-x ** 2 - y ** 2)

fig = plt.figure()
ax = mplot3d.Axes3D(fig)
ax.plot_surface(x, y, z, rstride=10, cstride=10, cmap='jet')
plt.savefig('matplotlib14.jpg')
```

![matplotlib14.jpg](https://vip1.loli.net/2020/06/16/DrMjR6otmZXza5y.jpg)

之后的图形绘制将会用到 seaborn 或 pandas 。

### 1.9 直方图和密度图

直方图和密度图，都是矩阵图或者柱形图的变种，区别在与数据是否具有连续性。

直方图是一种条形图，用于给出值得频率的离散显示。数据点被分成离散的，均匀间隔的箱，并且绘制每个箱中数据点的数量，我们可以使用 Series 的 plot.hist 工具制作直方图。

参数|说明
--|:--:
x|这个参数是指定每个bin(箱子)分布的数据,对应x轴
bins|这个参数指定bin(箱子)的个数,也就是总共有几条条状图
normes|这个参数指定密度,也就是每个条状图的占比例比,默认为1
color|这个指定条状图的颜色

下面是一个简单的直方图。

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from pandas import Series, DataFrame

np.random.seed(666)
s = Series(np.random.randn(1000))
s.hist(rwidth=0.9, bins=5, histtype='stepfilled')

plt.savefig('matplotlib15.jpg')
```

![matplotlib15.jpg](https://vip1.loli.net/2020/06/16/qs3RYEwmXtIQHPr.jpg)

密度图是一种与直方图相关的图表类型，他通过计算可能产生观测数据的连续概率分布估计而产生，通常是一种类似正态分布的简单分布，密度图也被称为内核密度估计图（KDE）。

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from pandas import Series, DataFrame

s = Series(np.random.randn(1000))
s.plot(kind='kde')

plt.savefig('matplotlib16.jpg')
```

![matplotlib16.jpg](https://vip1.loli.net/2020/06/16/Rh8gwQcF5pTYlLz.jpg)

此外，还可以使用 distplot 绘制直方图和连续密度估计。

### 1.10 箱型图

箱型图、小提琴图和蜂群图都是类似用作显示一组数据分散情况资料的统计图，主要用于反映原始数据分布的特征，还可以进行多组数据分布特征的比较，其中小提琴图和蜂群图是箱型图的变种，可用作箱型图的替代，下面是三种图像的简单图片，因时间限制不做详述。

```python
from sklearn.datasets import load_iris
import seaborn
import matplotlib.pyplot as plt

bunch = load_iris()
x = bunch.data[:, 0]
y = bunch.target

seaborn.boxplot(x=y, y=x)
plt.savefig('matplotlib17.jpg')
```

![matplotlib17.jpg](https://vip1.loli.net/2020/06/16/3lfg7MkqF5JenGz.jpg)

#### -小提琴图

```python
from sklearn.datasets import load_iris
import seaborn
import matplotlib.pyplot as plt

bunch = load_iris()
x = bunch.data[:, 0]
y = bunch.target

seaborn.violinplot(x=y, y=x)
plt.savefig('matplotlib18.jpg')
```

![matplotlib18.jpg](https://vip1.loli.net/2020/06/16/s7KP2MhLTkANJFV.jpg)

#### -蜂群图

```python
from sklearn.datasets import load_iris
import seaborn
import matplotlib.pyplot as plt

bunch = load_iris()
x = bunch.data[:, 0]
y = bunch.target

seaborn.swarmplot(x=y, y=x)
plt.savefig('matplotlib19.jpg')
```

![matplotlib19.jpg](https://vip1.loli.net/2020/06/16/Jr2pml3xEFPnIY4.jpg)

### 1.11 小结

matplotlib 作为 Python 数据可视化的泰斗，你可以仅仅只用一丢丢甚至一行命令行来创建一个简单的平面图，除了可以方便的绘制折线图、条形图、柱形图散点图等基础图形，还可以绘制复杂的图形。

## 2 **数据可视化 -- pyechart 篇**

