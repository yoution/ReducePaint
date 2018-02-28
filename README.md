# PaintReduce
研究compositing和paint的时候发现有些概念特别容易混在一起，所以重新研究了下减少paint的情况

## 例子
* [`demo1`](https://codepen.io/yoution/pen/aqPLeB)
![demo1](./images/demo1.png)
蓝色方块和绿色方块各自的paintLayer由于`will-change`的存在，生成各自对应的graphicsLayer   
绿色方块触发hover后:
![demo1_1](./images/demo1_1.png)
可以发现没有进行paint过程

图中为蓝色方块`will-change`生成graphicsLayer，绿色方块由于overlay原因

处理will-change属性外，其他样式也能达到相同的效果
如backface-visibility: hidden;

24801
1 kCompositingReason3DTransform
5 kCompositingReasonIFrame 
6 kCompositingReasonBackfaceVisibilityHidden
7 kCompositingReasonActiveAnimation
13 kCompositingReasonVideoOverlay
14 kCompositingReasonWillChangeCompositingHint

platform/graphics/PaintInvalidationReason.h
