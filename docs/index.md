!!! tip "提示"
    你好呀，欢迎来到 fuzzy_han's document。
# welcome to fuzzy_han's website

```python
print("hello fuzzy han")
```

```c
#include <stdio.h>
int main(){
    printf("hello fuzzy han"\n);
    return 0;
}
```

```cpp
#include <iostream>
using namespace std;
int main(){
    cout<<"hello fuzzy han"<<endl;
    return 0;
}
```
[实时渲染公式word latex等格式](https://snip.mathpix.com/)
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>User Feature Visualization</title>
    <script src="https://cdn.jsdelivr.net/npm/echarts@5.4.3/dist/echarts.min.js"></script>
</head>
<body>
    <div id="chart" style="width: 800px; height: 400px;"></div>
    <script type="text/javascript">
        var chartDom = document.getElementById('chart');
        var myChart = echarts.init(chartDom);
        var option;

        option = {
            title: {
                text: 'User Feature Analysis'
            },
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                    type: 'shadow'
                }
            },
            legend: {
                data: ['Active Days Ratio', 'Last Active Interval (days)', 'Avg Daily Interactions']
            },
            xAxis: {
                type: 'category',
                data: ['U9', 'U22405', 'U16', 'U48420']
            },
            yAxis: {
                type: 'value'
            },
            series: [
                {
                    name: 'Active Days Ratio',
                    type: 'bar',
                    data: [0.5, 0.6, 0.4, 0.7],
                    itemStyle: { color: '#5470c6' }
                },
                {
                    name: 'Last Active Interval (days)',
                    type: 'bar',
                    data: [5, 3, 7, 2],
                    itemStyle: { color: '#91cc75' }
                },
                {
                    name: 'Avg Daily Interactions',
                    type: 'bar',
                    data: [2.5, 3.0, 1.8, 4.0],
                    itemStyle: { color: '#fac858' }
                }
            ]
        };

        myChart.setOption(option);
    </script>
</body>
</html>
<!-- <span id="busuanzi_container_page_pv">本文总阅读量<span id="busuanzi_value_page_pv"></span>次</span> -->
<span id="busuanzi_container_site_uv">本站总访客数<span id="busuanzi_value_site_uv"></span>次</span>
