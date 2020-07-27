# 在react中使用echarts图表插件

##### 1.首先打开npm官网，输入echarts,我们会看见专为react配置的echarts包

![1543662653366](C:\Users\鲍瑞\AppData\Local\Temp\1543662653366.png)

##### 2.我们这里选择第二个点进去安装

```
npm install --save echarts 

npm install --save echarts-for-react 
```

没有科学上网工具的建议使用淘宝的cnpm安装

##### 3.在react中导入echarts包

```react
import ReactEcharts from 'echarts-for-react'; 
```

这里也可以按需加载相应的图表

##### 4.使用echarts（柱形图）

```react
getOption = (time, num) => {

    let option = {
      //背景颜色
      backgroundColor: '#2d343a',
      //标题
      title: {
        text: '分时段实际节拍',
        textStyle: {
          //字体颜色
          color: '#fefefe',
          //字体大小
          fontSize: '30',
        },
        //padding: [10, 0, 20, 100],
      },
      //x轴
      xAxis: {
        type: 'category',
        // x轴的字体样式
        axisLabel: {
          show: true,
          textStyle: {
            color: '#fff',
            fontSize: '16',
          },
        },
        //控制网格线是否显示
        splitLine: {
          show: true,
          //网格线颜色
          lineStyle: {
            color: ['#272c34'],
            type: 'solid',
            width: 2,
          },
        },
        // x轴的颜色和宽度
        axisLine: {
          lineStyle: {
            color: '#272c34',
            //width: 3,   //这里是坐标轴的宽度,可以去掉
          },
        },
        //这里传入一个数组，作为x轴数值，比如时间
        data: time
      },
      //y轴
      yAxis: {
        type: 'value',
        //最小值设为1以保持整数，刻度值不会再出现小数
        minInterval:1,
        axisLabel: {
          show: true,
          textStyle: {
            color: '#fff',
            fontSize: '16',
          },
        },
        //控制网格线是否显示
        splitLine: {
          show: true,
          //网格线颜色
          lineStyle: {
            color: ['#272c34'],
            type: 'solid',
            width: 2,
          },
        },
        //坐标轴线
        axisLine: {
          lineStyle: {
            color: '#272c34',
            //width: 3,   //这里是坐标轴的宽度,可以去掉
          },
        },
      },
      tooltip: {
        trigger: 'axis',
      },
      series: [
        {
          data: num,
          type: 'bar',
          barWidth: 20,
          itemStyle: {
            normal: {
              //柱子颜色
              color: '#6ab681',
              //数值显示
              label: {
                show: true, //开启显示
                position: 'top', //在上方显示
                textStyle: {
                  //数值样式
                  color: '#6ab681',
                  fontSize: 16,
                },
              },
            },
          },
        },
      ],
    };
    return option;
  };
  
 //bar 柱形图 在render函数中的return返回值引用
<ReactEcharts 
//柱形图具体样式，传入纵轴和横轴的值，可以绑定在state上实现动态刷新
option={this.getOption(time, num)} 
//控制柱形图具体高宽
style={{ height:5000px,width:300px}} />
```

