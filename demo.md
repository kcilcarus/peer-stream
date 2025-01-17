# 点线面体

## 生成 POI（点）

```
ps.emitMessage([
    "spawn-POI",
    "location:X=0 Y=0 Z=0", // cm
    "icon:\uE998",  // char
    "title:POI标题",    // string
    "color:R=1 G=1 B=1",   // 0~1
    "shape:2",  // 0、1、2
    "id:poi001"
].join('\r\n'));
```

- 图标：字体图标库中的任意字符。
- 标题：POI 图标旁边展示的标题文字。
- 颜色：POI 点的主题颜色。
- 坐标：三维空间中的 XYZ。
- 形状：0 菱形，1 圆形，2 圆角方形。

## 生成三维路径（线）

```
ps.emitMessage([
    "spawn-path",
    "points: X=0 Y=0 Z=1500; X=-1000 Y=0 Z=2000; X=0 Y=0 Z=0; X=1000 Y=0 Z=2000; X=0 Y=0 Z=1500",   // cm
    "location: X=0 Y=0 Z=0", // cm
    "width:100",    // cm
    "material:0",    // int
    "color: R=0 G=1 B=1 A=.5",   // 0~1
    "id:path001",
].join('\r\n'));
```

- 点集：分号";"分隔的三维坐标，提供一系列点坐标，连接成一段曲线。
- 位置：整体的三维坐标。
- 宽度：路径线条的宽度。
- 材质：选择样式编号。
- 颜色：材质的自定义 RGBA 通道。

## 生成区域围栏（面）

```
ps.emitMessage([
    "spawn-area",
    "points: X=1000 Y=0;  X=-809 Y=588;  X=309 Y=-951;  X=309 Y=951;  X=-809 Y=-588",   // cm
    "location: X=0 Y=2000 Z=0", // cm
    "height:300",    // cm
    "material:0",    // int
    "color: R=1 G=0 B=0 A=.4",   // 0~1
    "id:area001",
].join('\r\n'));
```

- 点集：以分号";"分隔的水平坐标 XY，代表二维区域的每个端点。
- 位置：三维空间中 XYZ 坐标。
- 高度：“围栏”的高度。
- 材质：选择区域轮廓的样式编号。
- 颜色：高亮的颜色（RGBA 通道）。

## 生成动画特效（面）

```
ps.emitMessage([
    "spawn-VFX",
    "location: X=0 Y=-2000 Z=0", // cm
    "scale:1.0",    // float
    "texture:1",    // int
    "period: 1.0",   // s
    "id:vfx001",
].join('\r\n'));
```

- 动图：选择图片编号。
- 位置：三维空间中 XYZ 坐标。
- 尺寸：无需传参，等于图片本身的宽高（1px=1cm）。
- 缩放：根据序列帧尺寸的缩放倍数。
- 周期：序列帧播放一遍的时间。

## 生成模型（体）

```
ps.emitMessage([
    "spawn-mesh",
    "location: X=-2000 Y=0 Z=0", // cm
    "scale:5.0",    // float
    "mesh:0",    // int
    "id:mesh001",
].join('\r\n'));
```

- 位置：三维空间中 XYZ 坐标。
- 缩放：模型整体的缩放倍数。
- 模型：选择模型编号，从 0 开始。

# 文档

## 参数格式

- 所有参数遵守类似字典的格式：
- 由换行符"\r\n"分隔每一行。
- 由于 UE 的原因，换行符必须使用"\r\n"，不能用常规的"\n"。
- 每行由冒号":"分隔键值对。
- 键和值两端没有空白字符。

## 鼠标操作

- 单击： 点击事件。
- 左键拖拽：平移。
- 右键拖拽：绕焦点旋转。
- 中间： 更新焦点。
- 滚轮： 缩放。
