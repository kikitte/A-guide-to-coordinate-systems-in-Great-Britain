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

- 

