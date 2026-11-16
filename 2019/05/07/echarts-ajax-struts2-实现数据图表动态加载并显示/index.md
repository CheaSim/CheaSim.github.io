# echarts+ajax+struts2 实现数据图表动态加载并显示

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2019/05/07/echarts-ajax-struts2-%E5%AE%9E%E7%8E%B0%E6%95%B0%E6%8D%AE%E5%9B%BE%E8%A1%A8%E5%8A%A8%E6%80%81%E5%8A%A0%E8%BD%BD%E5%B9%B6%E6%98%BE%E7%A4%BA/
发布日期：2019-05-07
更新日期：2019-05-07





# echarts+ajax+struts2 实现数据图表动态加载并显示

## echarts

百度出品的良心可视化数据js库。

### 简单小例子

12345678910111213141516171819202122232425262728293031323334353637383940414243444546474849505152535455565758596061626364656667686970717273    图表分析        // 基于准备好的dom，初始化echarts实例    var myChart = echarts.init(document.getElementById('main'));    // 指定图表的配置项和数据    option = {        backgroundColor: '#2c343c',        visualMap: {            show: false,            min: 80,            max: 600,            inRange: {                colorLightness: [0, 1]            }        },        series : [            {                name: '访问来源',                type: 'pie',                radius: '55%',                data:[                    {value:235, name:'视频广告'},                    {value:274, name:'联盟广告'},                    {value:310, name:'邮件营销'},                    {value:335, name:'直接访问'},                    {value:400, name:'搜索引擎'}                ],                roseType: 'angle',                label: {                    normal: {                        textStyle: {                            color: 'rgba(255, 255, 255, 0.3)'                        }                    }                },                labelLine: {                    normal: {                        lineStyle: {                            color: 'rgba(255, 255, 255, 0.3)'                        }                    }                },                itemStyle: {                    normal: {                        color: '#c23531',                        shadowBlur: 200,                        shadowColor: 'rgba(0, 0, 0, 0.5)'                    }                }            }        ]    };    // 使用刚指定的配置项和数据显示图表。    myChart.setOption(option);

echarts+ajax+struts2 实现数据图表动态加载并显示

https://www.cheasim.com/%E5%BC%80%E5%8F%91/2019/05/07/echarts-ajax-struts2-%E5%AE%9E%E7%8E%B0%E6%95%B0%E6%8D%AE%E5%9B%BE%E8%A1%A8%E5%8A%A8%E6%80%81%E5%8A%A0%E8%BD%BD%E5%B9%B6%E6%98%BE%E7%A4%BA.html

作者
CheaSim

发布于
2019-05-07

更新于
2019-07-11

许可协议

#[开发](https://www.cheasim.com/tags/%E5%BC%80%E5%8F%91/)[ajax](https://www.cheasim.com/tags/ajax/)[struts2](https://www.cheasim.com/tags/struts2/)[echarts](https://www.cheasim.com/tags/echarts/)




