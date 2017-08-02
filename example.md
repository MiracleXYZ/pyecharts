# More Example

用极坐标系画出一个爱心
```python
import math
from pyecharts import Polar

data = []
for i in range(101):
    theta = i / 100 * 360
    r = 5 * (1 + math.sin(theta / 180 * math.pi))
    data.append([r, theta])
hour = [i for i in range(1, 25)]
polar = Polar("极坐标系示例", width=1200, height=600)
polar.add("Love", data, angle_data=hour, boundary_gap=False,start_angle=0)
polar.show_config()
polar.render()
```
![example-0](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-0.png)


用极坐标系画出一朵小花
```python
import math
from pyecharts import Polar

data = []
for i in range(361):
    t = i / 180 * math.pi
    r = math.sin(2 * t) * math.cos(2 * t)
    data.append([r, i])
polar = Polar("极坐标系示例", width=1200, height=600)
polar.add("Flower", data, start_angle=0, symbol=None, axis_range=[0, None])
polar.show_config()
polar.render()
```
![example-1](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-1.png)


还可以给小花涂上颜色
```python
import math
from pyecharts import Polar

data = []
for i in range(361):
    t = i / 180 * math.pi
    r = math.sin(2 * t) * math.cos(2 * t)
    data.append([r, i])
polar = Polar("极坐标系示例", width=1200, height=600)
polar.add("Color-Flower", data, start_angle=0, symbol=None, axis_range=[0, None],
          area_color="#f71f24", area_opacity=0.6)
polar.show_config()
polar.render()
```
![example-1-1](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-1-1.png)


用散点图画出一个爱心
```python
from pyecharts import Scatter

scatter = Scatter("散点图示例", width=800, height=480)
v1 ,v2 = scatter.draw("../images/love.png")
scatter.add("Love", v1, v2)
scatter.render()
```
![example-2](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-2.png)


用散点图画出一个火辣的 Bra
```python
from pyecharts import Scatter

scatter = Scatter("散点图示例", width=1000, height=480)
v1 ,v2 = scatter.draw("../images/cup.png")
scatter.add("Cup", v1, v2)
scatter.render()
```
![example-3](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-3.png)


用散点图画出一个性感的 Bra
```python
from pyecharts import Scatter

scatter = Scatter("散点图示例", width=1000, height=480)
v1 ,v2 = scatter.draw("../images/cup.png")
scatter.add("Cup", v1, v2, label_color=["#000"])
scatter.render()
```
![example-4](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-4.png)


某地最低温和最高气温折线图
```python
from pyecharts import Line

attr = ['周一', '周二', '周三', '周四', '周五', '周六', '周日', ]
line = Line("折线图示例")
line.add("最高气温", attr, [11, 11, 15, 13, 12, 13, 10], mark_point=["max", "min"], mark_line=["average"])
line.add("最低气温", attr, [1, -2, 2, 5, 3, 2, 0], mark_point=["max", "min"],
         mark_line=["average"], yaxis_formatter="°C")
line.show_config()
line.render()
```
![example-5](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-5.gif)


饼图嵌套
```python
from pyecharts import Pie

pie = Pie("饼图示例", title_pos='center', width=1000, height=600)
pie.add("", ['A', 'B', 'C', 'D', 'E', 'F'], [335, 321, 234, 135, 251, 148], radius=[40, 55],is_label_show=True)
pie.add("", ['H', 'I', 'J'], [335, 679, 204], radius=[0, 30], legend_orient='vertical', legend_pos='left')
pie.show_config()
pie.render()
```
![example-6](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-6.png)


饼图再嵌套
```python
import random
from pyecharts import Pie

attr = ['A', 'B', 'C', 'D', 'E', 'F']
pie = Pie("饼图示例", width=1000, height=600)
pie.add("", attr, [random.randint(0, 100) for _ in range(6)], radius=[50, 55], center=[25, 50],is_random=True)
pie.add("", attr, [random.randint(20, 100) for _ in range(6)], radius=[0, 45], center=[25, 50],rosetype='area')
pie.add("", attr, [random.randint(0, 100) for _ in range(6)], radius=[50, 55], center=[65, 50],is_random=True)
pie.add("", attr, [random.randint(20, 100) for _ in range(6)], radius=[0, 45], center=[65, 50],rosetype='radius')
pie.show_config()
pie.render()
```
![example-7](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-7.gif)


某地的降水量和蒸发量柱状图
```python
from pyecharts import Bar

attr = ["{}月".format(i) for i in range(1, 13)]
v1 = [2.0, 4.9, 7.0, 23.2, 25.6, 76.7, 135.6, 162.2, 32.6, 20.0, 6.4, 3.3]
v2 = [2.6, 5.9, 9.0, 26.4, 28.7, 70.7, 175.6, 182.2, 48.7, 18.8, 6.0, 2.3]
bar = Bar("柱状图示例")
bar.add("蒸发量", attr, v1, mark_line=["average"], mark_point=["max", "min"])
bar.add("降水量", attr, v2, mark_line=["average"], mark_point=["max", "min"])
bar.show_config()
bar.render()
```
![example-8](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-8.png)


加个 datazoom
```python
bar = Bar("柱状图示例")
bar.add("蒸发量", attr, v1, mark_line=["average"], mark_point=["max", "min"])
bar.add("降水量", attr, v2, mark_line=["average"], mark_point=["max", "min"],
        is_datazoom_show=True, datazoom_range=[50, 80])
bar.show_config()
bar.render()
```
![example-8-1](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-8-1.gif)


各类电影中"好片"所占的比例
```python
from pyecharts import Pie

pie = Pie('各类电影中"好片"所占的比例', "数据来着豆瓣", title_pos='center')
pie.add("", ["剧情", ""], [25, 75], center=[10, 30], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None, )
pie.add("", ["奇幻", ""], [24, 76], center=[30, 30], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None, legend_pos='left')
pie.add("", ["爱情", ""], [14, 86], center=[50, 30], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["惊悚", ""], [11, 89], center=[70, 30], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["冒险", ""], [27, 73], center=[90, 30], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["动作", ""], [15, 85], center=[10, 70], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["喜剧", ""], [54, 46], center=[30, 70], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["科幻", ""], [26, 74], center=[50, 70], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["悬疑", ""], [25, 75], center=[70, 70], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None)
pie.add("", ["犯罪", ""], [28, 72], center=[90, 70], radius=[18, 24],
        label_pos='center', is_label_show=True, label_text_color=None, is_legend_show=True, legend_top="center")
pie.show_config()
pie.render()
```
![example-9](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-9.png)


用极坐标系画出一个蜗牛壳
```python
import math
from pyecharts import Polar

data = []
for i in range(5):
    for j in range(101):
        theta = j / 100 * 360
        alpha = i * 360 + theta
        r = math.pow(math.e, 0.003 * alpha)
        data.append([r, theta])
polar = Polar("极坐标系示例")
polar.add("", data, symbol_size=0, symbol='circle', start_angle=-25, is_radiusaxis_show=False,
          area_color="#f3c5b3", area_opacity=0.5, is_angleaxis_show=False)
polar.show_config()
polar.render()
```
![example-10](https://github.com/chenjiandongx/pyecharts/blob/master/images/example-10.png)