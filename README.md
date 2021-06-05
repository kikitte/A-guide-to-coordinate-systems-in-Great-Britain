# A-guide-to-coordinate-systems-in-Great-Britain

## 1    简介

### 1.1    谁应当阅读这本小册子

这本小册子的目标人群为：精通除了大地测量学之外领域的其他人、需要了解坐标系统的概念来为处理坐标数据服务的人、需要大不列颠地区的制图坐标系统信息的人(mapping coordinate system)。该书介绍了：

- 地球坐标系(terrestrial coordinate system)的基本概念

  地面坐标系是被设计用来表达地球表面物体位置的坐标地系统。

- 全球定位系统(GPS)和英国地形测量局(Ordance Survey, OS)制图中用到的坐标系统，以及他们是如何彼此联系的。

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

当你观察地球上陆地表面和海洋表面细节时，会发现地球的形状不规则并且复杂。如果你将这些细节用于地图制图，你需要一个地球形状的简单模型，有时候这被成为“地球的画像”（figure of the Earth），且坐标系统将会基于此构建。紧接着相对这个简单的形状可以确定这些细节的位置来构建整个地球画卷。

大地测量学，所有制图和导航所以来的科学，其首先要确定简化的地球画像的形状和大小，接着要确定地球陆地表面各种要素的位置，从板块、海岸线、山脉，到测量和制图的控制标志。Hence geodesists provide the fundamental ‘points of known coordinates’ that cartographers and navigators take as their starting point. 大地测量学的第一个问题，即“什么是最适合地球的最简单、最基础的形状？”。只有在完成这个之后，我们才能将它作为一个参考面，这是我们测量地表是将会遵守的。

对于这个问题大地测量学家有两个非常有用答案：椭球(ellipsoids)和大地水准面(geoid)。为了真正理解坐标系统，你首先需要理解这些概念。

### 椭球(Ellipsoids)

地球非常接近球形。然而它有一个微笑的赤道隆起(equatorial bulge)使得赤道半径大约比极地半径长了千分之一。因此最能接近地球的几何形状是双轴椭球(biaxial ellipsoid)，这是一个将椭球环绕其短轴旋转得到的形状（less exactly, it is the shape obtained by squashing a sphere slightly along one axis）。椭球的短轴与地球旋转轴几乎相同。

因为椭球的形状不能完美的匹配地球，因此有许多不同的椭球被使用，有些被设计为整个地球的最佳适配（全局最优），有些只是局部地区最适配（局部最优）。例如全球定位系统GPS使用的一个被成为CRS80的椭球，该椭球为整个地球的最佳适配。在不列颠的地图至途中使用的椭球为Airy 1830椭球，被设计成只是在不列颠达到最佳适配，它比CRS80椭球更好但是不适用于地球上的其他区域。。所以多种多样的椭球被使用在不同的大小和形状的区域中，当然这些椭球的朝向和相对地球的位置也不一样。现代的趋势是为了考虑兼容性在任何地方都是用CRS80椭球。虽然局部最佳的椭球已经是一种过时的方式，但是它仍然比较重要因为它已经在国家制图坐标系统中被使用（指不列颠，并不是中国）。

