# A-guide-to-coordinate-systems-in-Great-Britain

## 1    简介

### 1.1    谁应当阅读这本小册子

这本小册子的目标人群为：精通除了大地测量学之外领域的其他人、需要了解坐标系统的概念来为处理坐标数据服务的人、需要大不列颠地区的制图坐标系统信息的人(mapping coordinate system)。该书介绍了：

- 地球坐标系(terrestrial coordinate system)的基本概念

  地面坐标系是被设计用来表达地球表面物体位置的坐标地系统。

- 全球定位系统(GPS)和英国地形测量局(Ordance Survey)制图中用到的坐标系统，以及他们是如何彼此联系的。

尽管这本小册子主要是针对GPS定位系统，但是其中的概念和技术也可以被应用于其他全球卫星导航系统(Global Navigation Satellite System, GNSS)中, 例如俄罗斯的GLONASS、欧洲的Galileo和中国北斗卫星导航系统(BDS)。

大地测量学要解决的问题，包括其他事情，都包含地球坐标系统的定义。对于坐标的使用通常都没有注意到这一点的存在，或者他们需要为了正确的使用错表需要知晓大地测量的基础概念。这个小册子解释了这些概念。如果你的工作中会拥戴地表上空间点的位置，想知道以下任何问题的答案，或者你不理解这些问题，这个小册子是给你提供这些答疑一个好的开始：

- 大地测量学家是如何定义覆盖大范围的正确的坐标系统？这个工作难在哪里？为什么我们不能对所有定位需求只使用一个简易的坐标系统。
- WGS84到底是个什么东西？它有多精确？WGS84如何于地图坐标联系在一起？为什么其他的全球定位系统与WGS84如此接近。为什么有这么多的缩略语用来描述GPS定位系统。
- How is the Ordnance Survey National Grid defined? How does OSGB36 relate to the National  Grid? Why does it seem to be difficult to relate the National Grid coordinates to GPS coordinates?  How are grid references converted to latitude and longitude coordinates? （TODO）
- 为什么坐标系统需要用到椭球？为什么有许多不同的椭球？为什么很难将坐标从一个椭球转换到另外一个椭球？椭球与基准面相同吗？平均海平面高程和椭球高程差别在那里？
- 为什么不同坐标系统的变换(transformation)是不精确的？GPS坐标是如何精确的与National Grid和平均海平面高相关联。

### 1.2    一些关于坐标系统的谬误

- 谬误一："地表上的点有唯一的经度和维度"

  出于混合了科学与历史偶然的多种原因（For Reasons that are a mixture of valid science and historical accident），没有一个统一的经纬度坐标系统。零经度（中央经线）有很多不同的经线，零纬度（赤道面）可以对应许多不同的圆。通常前者经过格林尼治附近的某个地方，后者通常在rotational equator的附近。在这本小册子中涉及到的经纬度坐标系统也有许多难以察觉的差异。

  结果就是 一个点的坐标在不同经纬度坐标系统下的差距可以超过200m。在一些应用中这样的误差大小可以是很重要的，所以知晓正在使用的坐标系统及其定义是很重要的。

- 谬误二：“水平面就是水准面(level surface)”

  当然，它不是，因为地球时圆的----任何重力水平面(gravitationally)（比如杯子里的葡萄酒表面，或者平均海水面）的曲率应当如同地球曲率，所以它不能是平的（即它不能是几何意义上的平面）。除此之外，水准面有更复杂的形状----它不是想球体一样的简单的曲面。当我们说 "水准面" 我们指的是一个处处与重力方向垂直的表面。重力的方向大致上朝向地心，但是它的方向和大小以复杂原因在不同的地方存在着差异，即使是在很小的范围内。这些由地表质量不均匀分布造成的差异都很小，以致与如果不使用特殊的测量仪器则无法注意到。因此水准面都很坑洼和复杂。

- 谬误三：“地面点的真实坐标不会变化”

  他们会变化，这是由于地球持续的变形运动（Note：变形运动不是大陆漂移）。地面上的点由于太阳和月亮带来的潮汐的影响每天相对于地心移动的高度甚至能达到正负1m。大陆之间一年的相对移动甚至可以达到10cm，这些移动对于制图来说影响很大，因为它是不断持续的过程，在50年后大陆之间相对移动可以达到50m。许多其它的效应可以被观察到： the sinking of Britain when the tide comes in over the continental shelf (a few centimetres), the sinking of inland areas under a weather system ‘high’ (about 5 millimetres), and the rising of the land in response to the melting of the last Ice Age (about 2 millimetres per year in Scotland, up to 1 centimetre per year in Scandinavia)。总的来说，随着基于单个坐标系统下地球上区域面积的增大， 地球这种动态变化带来的影响也越来越显著。

  现代的趋势是使用全球坐标系统，即使是局部的应用场景。因此注意到在全球坐标系统下我们所站的地面是持续移动的十分重要。

- 谬误四：在不同的坐标系统之间有精确的数学公式进行变换。

  精确的公式只适用于完美的几何学领域，不是用于真实世界上的地表的点坐标。基于某个坐标系统下某个点的已知坐标是从在一大堆假设条件下通过大量观测平均得来。观测和假设可能是接近正确的也可以是准确性存疑的，尤其是这个点是在很久之前被定位的。因为它是坐标，由于沉降、大陆漂移和其他作用 它也是会移动的。

  所造成的结果就是到目前位置两个坐标系统的关系必须在地表上被观察到，并且这种观察容易造成主观误差。因此从一个坐标系统的坐标转换到另一个系统只存在拟合模型。第一个回答的问题时 我需要何种精度？通常如果需要低精度（比如说5到10米），这种坐标系统之间的变换则简单且容易。如果精度需求很高(比如说在任意地点上达到1厘米至半米)，则需要更多的转换过程。在任何情况下，变换过程应当有规定的精度级别。

- 

## 2    地球的形状

### 第一个大地测量学的问题

当你观察地球上陆地表面和海洋表面细节时，会发现地球的形状不规则并且复杂。如果你将这些细节用于地图制图，你需要一个地球形状的简单模型，有时候这被成为“地球的形状”（figure of the Earth），且坐标系统将会基于此构建。紧接着相对这个简单的形状可以确定这些细节的位置来构建整个地球画卷。

大地测量学，所有制图和导航所以来的科学，其首先要确定简化的地球画形状和大小，接着要确定地球陆地表面各种要素的位置，从板块、海岸线、山脉，到测量和制图的控制标志。Hence geodesists provide the fundamental ‘points of known coordinates’ that cartographers and navigators take as their starting point. 大地测量学的第一个问题，即“什么是最适合地球的最简单、最基础的形状？”。只有在完成这个之后，我们才能将它作为一个参考面，这是我们测量地表是将会遵守的。

对于这个问题大地测量学家有两个非常有用答案：椭球(ellipsoids)和大地水准面(geoid)。为了真正理解坐标系统，你首先需要理解这些概念。

### 椭球(Ellipsoids)

地球非常接近球形。然而它有一个微笑的赤道隆起(equatorial bulge)使得赤道半径大约比极地半径长了千分之一。因此最能接近地球的几何形状是双轴椭球(biaxial ellipsoid)，这是一个将椭球环绕其短轴旋转得到的形状（less exactly, it is the shape obtained by squashing a sphere slightly along one axis）。椭球的短轴与地球旋转轴几乎相同。

因为椭球的形状不能完美的匹配地球，因此有许多不同的椭球被使用，有些被设计为整个地球的最佳适配（全局最优），有些只是局部地区最适配（局部最优）。例如全球定位系统GPS使用的一个被成为CRS80的椭球，该椭球为整个地球的最佳适配。在不列颠的地图至途中使用的椭球为Airy 1830椭球，被设计成只是在不列颠达到最佳适配，它比CRS80椭球更好但是不适用于地球上的其他区域。。所以多种多样的椭球被使用在不同的大小和形状的区域中，当然这些椭球的朝向和相对地球的位置也不一样。现代的趋势是为了考虑兼容性在任何地方都是用CRS80椭球。虽然局部最佳的椭球已经是一种过时的方式，但是它仍然比较重要因为它已经在国家制图坐标系统中被使用（指不列颠，并不是中国）。

### 2.3    大地水准面(The Geoid)

如果我们想测量搞成，我们需要想象中的在我们下边的0高程表面，这是我们测量时需要参考的。任意点精确的高程为距离假想表面的垂直高度。即使我们用随意的、相对的术语讨论搞成，我们也是隐式地假设这个曲面存在。

递增的高程在地图上被认为是上坡和递减的高程在地图上被认为是下坡这两点事实暗含了高程参考表面必须是一个水准面，即在任何地方直角总是指向重力的方向。如果我们在整个世界的角度上谈论某个地方的高程很显然这个参考表面应当是封闭的形状，并且它会是类似于椭球形状的物体。它的具体形状可以通过满足其表面的任何一处与重力方向处处垂直这一条件而确定。就像在1.2中指出的，水准面并不是简单的几何形状。重力的方向尽管大致指向地球中心，但是在全球尺度乃至细微局部都因为复杂的原因而不同。这表明参考水准表面不是像椭球之类的简单的形状而是崎岖不平和复杂的。我们可以使用物理观测的方法确定水准面，比如精确重力测量。这是被称作重力测量的科学研究。

取决于何种高程被我们选择作为'zero height'，有任意数量的闭合水准面可以被我们选择作为全球高程参考表面，并且这种选择可以说是任意的。我们可以认为这些在地球地表面内部和外部的水准面就像洋葱的表层一样。每一个都对应于地球重力场的不同潜在能级，每一个尽管都是不规则形状，其高程却是常量。我们选择最接近地球所有海洋的平均表面的水准面作为高程参考表面。这是有意义的选项因为我们时沿海生物并且我们通常认为海平面的高程为0 。我们将这个不规则的三维形状叫做大地水准面(Geoid)。尽管它全部是想象出来的并且难于测量，但是它是唯一的表面：它是全球范围内最吻合平均海洋表面的水准面。这不同于椭球体，椭球体有很多区域与地球并不吻合。

大地水准面与椭球体的形状非常接近--我们可以定义最优的椭球体使得椭球体表面与大地水准面的匹配程度优于200m。然而这就是在椭球上我们能做到的最优适配， and usually we want to know our height much better than that。大地水准面在世界范围内其上的点的有相同的高程，并且它不会超过当地海平面几米的高度。这使得它成为全球定位系统垂直定位的理想参考平面。大地水准面在许多方面就像我们在2.1章节介绍的真实的地球形状一样，因为一个基础的水准面对于我们认识世界是必要的，它的存在就像我们对待强大的重力场一样。如果你想，在认识到地球的形状是圆的而不是平坦的之后要做的就是认识到这个形状是复杂的大地水准面形状而不是简单的圆。

#### 2.3.1 局部大地水准面

地图上的高程测量通常起始于平均海平面。这意味着一个不同的水准面被用来充当0高程参看平面--一个基于安放在制图区域当地验潮仪而不是全球平均海平面。对于大多数用途来说，这些局部参考表面可以被认为是与大地水准面平行，但是有整体误差，有时候达到2米。例如， heights in mainland Britain are measured relative to the tide-gauge in Newlyn, Cornwall, giving a reference surface which is about 80 centimetres below the Geoid。

是什么引起了全球平均海平面和局部海平面的不合常理的差异？我们知道纯水在不受干扰下构成水平面，所以这两者应该相同。但问题是海洋包围的海岸绝对不是不受干扰的。洋流(oceanic currents)、潮汐作用(effects of tide)、岸边的风、水温差异和纯度 都导致了平均海平面与大地水准面的细微差距。所以平均海平面包含了轻微的丘陵和河谷，这些被术语海洋地表形状??(sea surface topology)。围绕着不列颠的海洋碰巧围绕成了河谷的形状，所以他们的（指不列颠）平均海平面大约比大地水准面低80厘米。不同的国家才用了不同的局部海平面作为他们的0高程定义。世界上不同的区域有许多不同的0高程参考面，它们基于都与真是的全球大地水准面平行。这些参考平面有时候被乘坐local geoids--大写的G可以不写。

## 3    什么是位置Position？

我们已经介绍了不规则的、动态的地球，椭球的概念以及用来描述其基本形状的大地水准面。现在我们想以一种简单的数字方式 确切地描述我们或者一些要素在地球上的位置，所以挑战在于如何定义一个坐标系统，其可以使用明确的一系列数字阐明任意地表要素的唯一并且精确的位置。在大地测量学、制图学和导航领域，位置代表在明确定义的坐标系统下的坐标，并且附加上这些坐标可呢存在的误差。我们是怎么拿到这些的呢？

这个问题的答案是本节所有内容的主题。在3.1中我们会学习到在工作中会碰到的不同类型的坐标(coordinates)，3.2和3.3中我们会接触到两个在创建地球坐标系统中必须的概念，这些概念将会告诉我们蕴含在一系列坐标中的更深的细节。

### 3.1    坐标的类型(The types of coordinates)

#### 3.1.1 經度、维度、椭球高

表示地球位置(terrestrial position)的做常用的方式是使用两个角度：經度和纬度。这些定义了在地球球体上的一个点。更准确的来说，他们在椭球体表面定义了一个临近球体的点。因此，在任何程度的精度条件下你必须知晓当前正在使用的椭球。

椭球和经纬度的关系很简单。一个經度对应南北方向的线条被称为大地经线，一个纬度对应东西方向的线条被称为纬圈(parallels)。椭球上的其中一个大地经线被选择作为中央经线并且给其赋值0經度。椭球上一点的經度为经过该点的经线与中央经线的夹角。通常經度被分成东西半球（半椭球，更精确地说）：从0度到西经180度、从0度到东经180度。椭球的赤道被选择作为0纬度的纬圈。点的纬度为过该点垂直于椭球的直线与赤道面的夹角。纬度同样被分成0到北纬90度和0到南纬90度，不管是在南或北90度纬度都是一个点----椭球的极点。

所以經度和纬度给定了在精确定义的椭球体表面上的位置。因为地表上真是的点通常是在椭球体表面以上（或者在其下面），我们需要第三个坐标，被称作椭球高，即从该点起沿着垂直于椭球体表面的直线到椭球体表面的距离。术语“椭球高” 实际上不常被使用，因为即使这个高度是接近于垂直测量，但是它并没有给出真实的高度因为不是相对于水准面。它真正做到的事以一种简单的几何方式给出一个点在椭球体表面以上或以下的精确的表达方式，这就是它的用意。

通过使用三个坐标：經度、纬度、高度 我们可以明确的相对于椭球体定位一个点。为了将这个点精确的转换到地表上，我们需要精确的知道椭球体与我们感兴趣区域的相对位置。



### 3.1.2    笛卡尔坐标

空间直角坐标是用于描述三维空间位置的非常简单的系统，使用三个互相垂直的坐标轴：X、Y、Z。三个坐标清晰地定义了在系统上的任何点。我们可是使用它来作为經度、纬度、椭球高的一个有效的替代用来表达同样精确的信息。

我们使用三个笛卡儿坐标轴与经纬度系统一起排布。X坐标轴位于椭球赤道面上并且经过中央经线（0經度）。X轴的负半部分经过180读經度。Y轴也同样位于赤道面上但是他经过东经90度，因此与X轴成直角。显然Y轴的负半部分经过西经90度。Z轴等同于椭球的极轴：正半部分经过北极，负半部分经过南极。因此它与X轴、Y轴都垂直。

很明显任何能唯一使用经纬度、椭球高表示的位置都可以使用唯一的三个笛卡尔坐标来表示，反之亦然。这两种等价系统之间的转换方式在附录B中提供。

必须清楚的认识到将经纬度转换到笛卡尔坐标，其转寒结果是相对于笛卡尔坐标轴的，这对于所使用的椭球来说是唯一的。他们不能与其它椭球或者没有应用坐标系统间变换 的笛卡尔坐标混淆（没有可比性）。当考虑将不同数据源的坐标放在一起使用时，需要小心一种名称的坐标系统可能会有多种实现，他们不一定会彼此兼容。

类似的，将笛卡尔坐标转换到经纬度椭球高，这个转换结果也是相对椭球而言的，并且也是相对于输入坐标的笛卡尔参考坐标系统而言的。他们在没有提前进行合适变化的情况下不能与任何其他的椭球或坐标系统一起使用。

### 3.1.3    大地水准面高

术语“椭球高”带有误解性因为参考椭球体上的一段距离并不一定意味着高程：点A可以比点B具有更大的椭球体高度，同时处于B的下坡位置。正如第二章中我们看到，这是因为椭球体表面不是水平的，所以椭球体上的一段距离根本就不是高程。大地水准面才是任何地方的参考表面。为了确保点A和点B之间相对高程的过渡，我们必须将地表到大地水准面的距离作为高程测量，而不是水准面。这种测量被叫做“正高”（orthometric height）"或者简单的说 大地水准面高。

椭球高和大地水准面高（正高）的关系为：

```mathematica
H = h + N
```

其中，N为椭球体和大地水准面差异（reasonably enough）。因为大地水准面是一个复杂的表面，取决于經度和纬度N因为复杂的方式而不同。用于任意特定的经纬度的查询表(lookup table)被叫做大地水准面模型。因此你需要大地水准面模型来将椭球高转换为大地水准面高，反之亦然。图5展示了点A和点B的这些量。A和B的正高差为

```mathematica
// TODO
```

因为GPS测定H和大地水准面模型测定N在相对意义上(附近两点之间的差值)比全球绝对意义上更精确。hAB会永远比hA或者hB更加精确。这是因为hA中大多数的误差也会在hB中出现，并且误差被使用两个量的差值移除。非常幸运我们真正感兴趣的是通常是hAB：我们想知道数对点的高差。

精确的大地水准面模型的开发对于提高高程坐标系统的精确程度是非常重要的。一个好的大地水准面模型能让我们使用GPS（产生椭球高）和方程（用来转换为椭球高）来确定正高。单独的GPS提供的椭球高提供给我们几何信息，但是并没有提供真正的高度因为它没有告诉我们重力场。对一个点而言不同的大地水准面模型将会产生不同的正高，即使椭球高（通过GPS确定）可能非常精确。因此正高应当与体使用的大地水准面模型一起提供。正如我们现在将看到的，即使是专门由水准测量方法建立和使用的高度坐标系也涉及大地水准面模型，尽管这可能没有明确说明。

### 3.1.4 平均海平面高

现在我们将关注英国地形测量局给不列颠岛制图时使用的大地水准面模型，尽管大多数测量人员可能不会马上想到这一点（Although most surveyors ight not immediately think of it as such)。它就是Ordnance Datum Newlyn (ODN)垂直坐标系统。英国地形测量局使用基于平均海平面的高程来对州进行制图。如果我们想要在测高中使用亚米级(sub-metre)的精度，但是这是一个不明确的表述，因为平均海平面(MSL)随着时间和地点的不同而不同，就像我们在2.3章节中提到。

ODN与由 the tide-gauge at NewlynCornwall在1915和1921年所测得的平均海平面相接近。以这个特殊的平均海平面作为0高程点的高程被叫做ODN高程(ODN heights)。ODN因此是一个在2.3章节中提到的局部大地水准面。ODN高程在 英国本土的所有等高线、sopt height、bench mark heights  中被使用。ODN高程在许多沿海岛屿中不可用，因为他们通过测潮站有自己4的平均海平面。

图6显示了MSL高程对比椭球高。它呈现了ODN高度为在延伸到陆地内部的平均海平面表面的垂直的距离。

那么在陆地下面连续的平均海水面有意味着什么？答案是在图6中以点线形式显示的表面事实上是局部大地水准面模型。小写的'g'表明局部大地水准面模型与全球大地水准面相对。它是在本世纪前半部分使用水准测量从Newlyn reference point测量得到的，测得了横跨不列颠的70万个水准点。既然我们已经知道了每个水准点之间的距离，根据ODN局部大地水转面，通过使用GPS测量Ordnace Survey水准点的高程，根据在该点的ODN模型我们可以得到大地水准面和椭球的差值N。

ODN正高已经成为了不列颠的国家标准，并且很可能会继续保持。理解ODN正高与通过现代重力测量得到的高程产生的差异的原因是重要的。这些差异可能达到1m，尽管方程2中的hab很可能只超过几厘米。有三个原因造成这种情况。

首先，ODN模型在测量时假设在Newlyn某个时间、某个地点的平均海平面等同于大地水准面。这是不真实的，真正的大地水准面是全球平均海平面的最佳匹配，不是在特定时间特定地点的平均海平面。平均海平面在大地水准面的各处不同，由于水流、温度、压力和密度的差异。这种现象被称为海洋表面地形（sea surface topolygon, SST）。这种效应只有在需要在超过一个国家的范围内比较不同正高的差异才重要；对于在不列颠内的所有应用来说这是不相关的。ODN参考表面是一个面向不列颠优化的局部大地水准面模型，并且他是最适合在不列颠使用的参考表面。

第二，因为ODN大地水准面模型只是将MSL绑定在一点上，它很可能会遭受到像水准测量那样从一个点进行长距离后的 "slope error"。整个模型有非常轻微的slope error已经被知晓了很久，即它或许相对于真实的大地水准面有偏移。这个误差在1000km的范围内大概能达到不超过20cm的程度。This error might conceivably be important for applications that require very precise relative heights of points over the whole of Britain. For any application restricted to a region 500 km or less in extent, it is very unlikely to be apparent.

第三点也是做重要的，当使用水准点来得到ODN高程时可能会混入误差。一些OSBM（ordance survay bench mark）早在1912年就开始被测量，从1970年代以来大多数没有被严格检查。因此我们必须关注由于原始测量限制导致的误差，或者水准点确定以来可能产生的移动。偶尔有轶事证据表明，在采矿导致地面塌陷的地方，基准点下沉误差达数米。这些类型的误差甚至可以影响局部高程测量，并且单个的水准点不应当在高精度工作中被信任。然而，ODN现在可以在无水准点参照的情况下被完全使用，使用OS Net通过精确的GPS测量。（省略一些不列颠的东西）。

### 3.1.5    Easting and northings

最后一中我们需要考虑的坐标类型是easting and nrothing，又称平面坐标(plane coordinate)、格网坐标(grid coordinate)、地图坐标(map coordinate)。这些坐标被用来相对地图确定位置，其使用二维平面表现地球曲面上的要素。到目前为止，"地图"已经变为计算机化的地里信息系统，但是基本的原则还是几乎相同。地图坐标使用简单的2D笛卡尔系统，他的两个坐标轴被称为eastings and nrothings。地图坐标是一个点使用了被叫做地图投影的标准公式从其椭球上的經度和纬度计算得来。这是与Ordnance Survey National Grid最经常相关的坐标类型。

地图投影不是一种完美的表达手法，因为在平面地图上现实曲面不可避免的产生拉伸形变和不连续(distortings and discontinuities)。因此，不同的地图投影被在不同的应用中被使用。在不列颠通常使用Ordnance Survey National Grid Projection和Universal Tranverse Mecator projection（UTM）。这些都是横轴墨卡托类型的投影。任何使用eastings and northings表示的坐标都应该伴随被用来创建他们的地图投影的精确描述。

在大地测量学中，地图坐标倾向于只用来做可视化表达的意图。当我们需要使用坐标进行计算的时候，我们会使用经纬度或者笛卡尔坐标系，随后如果需要的话将结果转换为地图坐标。这个工作流程与地理信息系统的相对，他们（GIS）会直接使用地图坐标进行许多计算任务。

### 3.2 我们需要基准面

我们已经见识使用不同类型的坐标到回答“什么是位置？”这个问题的方法：我们使用这些坐标类型其中一种或多种来表示地球上点和地表要素的位置。

不管我们使用何种类型的坐标，我们仍会需要一个合适的原点作为描述的坐标的参照。比如，我们无法使用笛卡儿坐标除非已经在所测量的地球定义好了坐标轴原点和坐标轴指向。这是定义坐标系统相对于地球的空间关系的一系列规则中的一个简单的例子。这个概念的一个概括性的名称叫地球参考框架（Terrestrial Reference System，TRS）或者大地基准（geodetic datum）。基准这个术语在测量人员中最被熟知，并且我们会在这个小册子中通篇使用。TRS是相同事物的一个更现代的术语。

为了使用3D笛卡儿坐标，需要3D基准面來设定三个轴：X、Y、Z。基准必须以某种方式描述三个坐标轴的原点的位置和这些坐标轴指向的方向，这些都是相对于地球表面描述。然后地球上每个点都会在新的笛卡儿坐标系下有唯一的一组(a set of)笛卡儿坐标。基准的定义是联系抽象的坐标和真实物理世界的桥梁。

为了使用经度、维度和椭球高坐标，我们以在3D笛卡儿坐标中用到的相同类型的基准作为起始。对于该基准，我们添加一个一笛卡儿原点为中心的参考椭球，该椭球的形状和大小被添加到基准的定义中。大小通常使用原点到赤道的距离作为定义，被叫做半长轴a(semi-major axis)。形状被诸多参数中的任意一个定义：半短轴b长度（semi-minor）（从原点到椭球极点的距离）、 the squared eccentricity e2、 or the inverse flattening 1/f（扁率）。事实上这些参数的表现形式在这里不太重要，这些每一个参数都表达了相同的信息：所选择的参考椭球的形状。

术语大地基准通常被采用来表示就像刚才描述的椭球类型的基准面（ellipsoidal type of datum）：一组3D笛卡儿坐标轴加上一个椭球，这使得3维笛卡儿坐标和经度、维度、椭球高可以相等地描述位置。基准的定义有8个参数构成：原点的三维坐标（3个参数）、坐标轴的指向（三个参数）、椭球的大小（一个参数）、椭球的形状（一个参数）。

然而也会有其它类型的大地基准。比如，用于正高测量的局部基准就非常简单：它由一个已知高程的水准点作为基础。（Note:  通过使用大地水准面模型，现代的高程基准正在与椭球基准越来越多地相结合。理想的状况是水平测量和垂直册来嗯都能使用单一的基准）。



