## KiCAD 元器件库

该仓库用于收集开源封装库以及自定义的元器件封装，并且还将从平台下载得到的符号/封装/3D 模型进行了

规范化的命名和分类，分类规则按照 JLC（嘉立创）以及 KiCAD 官方的规则为准，并且都转化为了 KiCAD v7.x 最新

的文件格式，该仓库将会长期持续维护并新增元器件。

所有文件，目录都以 `3rd_` 作为前缀，表示文件来自第三方，这样便于区别

我们自己添加的符号/封装和 KiCAD 官方的符号/封装，后续看到以 `3rd_` 开头的文件即可

知道这是我们自行添加的库文件，同样使用封装时也便于在 KiCAD 中搜索我们自行添加的库文件。

(1) symbols: 元器件符号库。

(2) footprints: 元器件封装库。

(3) 3dmodels: 元器件模型库。

(4) docs: 嘉立创封装命名标准文档，这里均按照该文档的命名和分类方式。

(5) kicad: 用于符号和封装测试的 KiCAD 工程。

## 封装命名规则

### 1.命名

(1) 使用下划线 `_` 分割不同的描述（或叫规格）类别。

(2) 使用横杆 `-` 分割相同描述类别的不同属性。

(3) `docs` 文件夹下放置有封装命名参考文档，该文档来自嘉立创的一些行业规范/规则，
除此之外也可以参考 [PCB封装命名规范](https://www.cnblogs.com/chengerccj/p/15004728.html) 
这篇博客。

**例如：**

(1) KEY-SMD_L4.2-W3.2-V_SKRPABE010

(2) QFN-88_L10.0-W10.0-P0.40

注意：其中的器件尺寸描述 `L4.2-W3.2` 和 `L10.0-W10.0`，单位默认是毫米 (mm)，

不包含引脚的长度，属于纯粹芯片封装外壳的尺寸。

### 2. 分类

符号涉及元器件管脚的功能，所以符号库需要按照元器件的类别及功能（例如 DCDC，MCU，Flash，Connector）

和产商名称（例如 ST，TI，NXP）进行分类。

封装分为通用封装（例如 QFN，QFP，SOT 等）和专用封装（例如 USB 封装）对于专用封装，

封装库需要按照元器件的功能（例如属于 DCDC，MCU，Connector）进行分类，但无需区分产商。

3D 模型和封装是深度绑定的，所以 3D 模型库分类规则和封装库的分类方法是相同的。

## 注意事项

由于从事器件制造的产生商很多，所以在物理上同一种封装可能存在多种命名，这实际上对我们制作封装，

管理封装带来了一些困难，在设计器件的封装时一定要认真查阅器件的不同厂商的数据手册，看看同一种封装

是不是有不同的命名，并且详细的对比它们的封装，看看是否存在差别。

例如下面几种封装总能把我们高的晕头转向，其中 SO 和 SOP 就是这样的例子。

![image.png](./da895b3a06858091.png)

## 使用方法

(1) 拉取 kicad-libs 文件夹，将 kicad-libs 文件夹及内部文件放置到自己喜爱的目录。

(2) 启动 KiCAD，在 KiCAD 的主页中的设置菜单选下下，点击 "管理符号库" 选项，在弹出的符号库管理面板中可以选择 "全局库"，也可以选择 "工程专用库"，将 kicad-libs/symbols 文件夹下用到的符号库相应的目录添加到 "符号库" 中。

![image.png](./20241113200410.jpg)

(3) 同理在 KiCAD 的主页中的设置菜单选下下，点击 "管理封装库" 选项，在弹出的封装库管理面板中可以选择 "全局库"，也可以选择 "工程专用库"，将 kicad-libs/footprints 文件夹下用到的封装库相应的目录添加到 "封装库" 中。

![image.png](./20241113200613.jpg)

(4) 在添加符号库和封装库的过程中可以将 KIPRJMOD 定义为 kicad-libs 所在的目录，在引用库的时候可以用 KIPRJMOD 代替 kicad-libs 所在的路径。

(5) 默认情况下封装是没有与封装对应的元件 3D 模型配对绑定的，所以需要自己在 PCB 设计完成后，在 PCB 编辑器的视图下选择 PCB 上的每一个封装，然后在封装属性上为封装指定对应的元件 3D 模型。

## 适用版本

KiCad 9.0.3 Release
Mon, Jul 7, 2025 
