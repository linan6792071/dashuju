<template>
   <div class="conright">
       <div class="ul-1">
           	<span id="t-left"></span>
						<span id="t-right"></span>
						<span id="b-left"></span>
						<span id="b-right"></span>
       <div id="mychartone"  :style="{width:'100%',height:'170px' }">

			</div>
   </div>
   <div class="ul-1">

           	<span id="t-left"></span>
						<span id="t-right"></span>
						<span id="b-left"></span>
						<span id="b-right"></span>
       <div id="mycharttwo"  :style="{width:'100%',height:'170px' }">

			</div>
   </div>

    <div class="ul-1">
           	<span id="t-left"></span>
						<span id="t-right"></span>
						<span id="b-left"></span>
						<span id="b-right"></span>
       <div id="mychartthree"  :style="{ width: '100%',height: '170px'}">

			</div>
   </div>
   </div>
</template>

<script>
import echarts from 'echarts'
    export default {
        name: "DataConRight",
        // data(){
        //     return {

        //     }
        // },
        props:["DataRight"],
        mounted(){
         this.one()
         this.two()

         this.three()
        },
        methods:{
two(){
    let myChart = echarts.init(document.getElementById("mycharttwo"));
        var  optiontwo = {
           title : {
          backgroundColor:'#051856',
         textStyle: {
                       fontSize:'20px',
                        color: '#fff',
                        width:'100%'
                    },
        text: '报警车辆TOP5',
        x:'left',

    },
      tooltip : {
        trigger: 'axis',
        axisPointer : {            // 坐标轴指示器，坐标轴触发有效
            type : 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
        },
        formatter: function (params) {
            var tar = params[0];
            return tar.name + ' : ' + tar.value + '辆';
        }
    },
       grid: {
        left: '3%',
        right: '5%',
        bottom: '1%',
        containLabel: true
    },
    xAxis: {
        type: 'category',
        data: ['NO.1', 'NO.2', 'NO.3', 'NO.4', 'NO.5'],

    },
    yAxis: {
        type: 'value',
        splitLine:{
            show:true  ,
             lineStyle:{
    color:'#32346c',
    width: 1
    }
        }
    },
    axisLabel: {
   color:'#bac0c0'
}  ,
    series: [{
        data: [28,22,20,16,12],
        type: 'bar',
         barWidth : 10,//柱图宽度
         itemStyle: {
                        //柱形图圆角，鼠标移上去效果，如果只是一个数字则说明四个参数全部设置为那么多
                        emphasis: {
                            barBorderRadius: 10
                        },

                        normal: {
                            //柱形图圆角，初始化效果
                            barBorderRadius:[10, 10, 10, 10],
                            color:'#2e83d4',
                            backgroundColor:"#121847",
                            label: {//是否展示
                                textStyle: {
                                    fontWeight:'bolder',
                                    fontSize : '12',
                                    fontFamily : '微软雅黑',
                                }
                            }
                        }
                    },

    }]
};
myChart.setOption(optiontwo);
},
one(){
     let myChart = echarts.init(document.getElementById("mychartone"));

    var optionone = {
         fontSize: 18,

    title : {
          backgroundColor:'#051856',
         textStyle: {
                       fontSize:'20px',
                        color: '#fff',
                    },
        text: '本月行驶里程TOP5',
        x:'left',

    },
    tooltip : {
        trigger: 'item',
        formatter: "{b} :<br> {c} ({d}%)"
    },
    calculable : true,
    series : [

        {
            type:'pie',
            radius :  [20, 70],
            center : ['50%', '65%'],
            roseType : 'area',
            data:
               this.DataRight.datarightone

        }
    ]
};
myChart.setOption(optionone);
    },
 three(){
                        let myChart = echarts.init(document.getElementById("mychartthree"));

let data = {
    "chart": [{
            month: "NO.1",
            value: 600,
            ratio: 14.89
        },

        {
            month: "NO.2",
            value: 500,
            ratio: 79.49
        },

        {
            month: "NO.3",
            value: 614,
            ratio: 75.8
        },

        {
            month: "NO.4",
            value: 442,
            ratio: 19.8
        },

        {
            month: "NO.5",
            value: 322,
            ratio: 44.5
        }

    ]
}


let xAxisMonth = [],
    barData = [],
    lineData = [];
for (let i = 0; i < data.chart.length; i++) {
    xAxisMonth.push(data.chart[i].month);
    barData.push({
        "name": xAxisMonth[i],
        "value": data.chart[i].value
    });
    lineData.push({
        "name": xAxisMonth[i],
        "value": data.chart[i].ratio
    });
}

var  optionthree = {
     title : {
          backgroundColor:'#051856',
         textStyle: {
                       fontSize:'20px',
                        color: '#fff',
                        width:'100%'
                    },
        text: '电池报警车辆TOP10',
        x:'left',

    },
    backgroundColor: "#020d22",
   grid: {
        left: '5%',
        right: '8%',
        bottom: '1%',
        containLabel: true
    },
    tooltip: {
        trigger: 'axis',
        axisPointer: {
            type: 'none'
        },
        formatter: function(params) {
            return params[0]["data"].name + "<br/>" + '报警次数: ' + params[0]["data"].value + '次';
        }
    },
    xAxis: [{
            type: 'category',
            show: false,
            data: ['3月', '4月', '5月', '6月', '7月', '8月'],
            axisLabel: {
                textStyle: {
                    color: '#b6b5ab',
                    fontSize:'5px'
                },

            }
        },
        {
            type: 'category',
            position: "bottom",
            data: xAxisMonth,
            boundaryGap: true,
            // offset: 40,
            axisTick: {
                show: false
            },
            axisLine: {
                show: false
            },
            axisLabel: {
                textStyle: {
                    color: '#b6b5ab'
                }
            }
        }

    ],
    yAxis: [{
        show: true,
        offset: 10,
        splitLine: {
            show: false,
            lineStyle: {
                color: "rgba(255,255,255,0.2)"
            }
        },
        axisTick: {
            show: false
        },
        axisLine: {
            show: true
        },
        axisLabel: {
            show: true,
            color: '#b6b5ab'
        }
    }, {
        show: false,
        type: "value",
        name: "合格率(%)",
        nameTextStyle: {
            color: '#ccc'
        },
        axisLabel: {
            color: '#ccc'
        },
        splitLine: {
            show: false
        },
        axisLine: {
            show: false
        },
        axisTick: {
            show: false
        }
    }],
    color: ['#e54035'],
    series: [{
            barWidth : 60,//柱图宽
            name: '训练人次',
            type: 'pictorialBar',
            xAxisIndex: 1,
            barCategoryGap: '-80%',
            // barCategoryGap: '-5%',
            symbol: 'path://d="M150 50 L130 130 L170 130  Z"',
            itemStyle: {
                normal: {
                    color: function(params) {
                        let colorList = [
                            'rgba(13,177,205,0.8)', 'rgba(29,103,182,0.6)',
                            'rgba(13,177,205,0.8)', 'rgba(29,103,182,0.6)',
                            'rgba(13,177,205,0.8)', 'rgba(29,103,182,0.6)'
                        ];
                        return colorList[params.dataIndex];
                    }
                },
                emphasis: {
                    opacity: 1
                }
            },
            data: barData,
        }
    ]

}
 myChart.setOption(optionthree);
       },
 four(){
      let myChart = echarts.init(document.getElementById("mychartfour"));
      var optionfour = {
      title : {
          backgroundColor:'#051856',
         textStyle: {
                       fontSize:12,
                        color: '#fff',
                        width:'100%'
                    },
        text: '车辆充电高峰时间',
        x:'left',

    },
    tooltip: {
        trigger: 'axis',
        axisPointer: {
            lineStyle: {
                color: '#57617B'
            }
        }
    },
     grid: {
        left: '3%',
        right: '3%',
        bottom: '1%',
        containLabel: true
    },
    xAxis: [

        {
        type: 'category',
        nameTextStyle:{fontSize:4},
        boundaryGap: false,
        axisLine: {
            lineStyle: {
                color: '#0E2A43'
            }
        },
        axisLabel: {
            margin: 10,

   interval:0,
   rotate:40  ,
            textStyle: {
                fontSize: 8,
                color: '#D5CBE8'
            }
        },
        axisTick: {
            show: false
        },
        data: ['0时','1时','2时','3时','4时','5时','6时','7时','8时','9时','10时','11时','12时','13时','14时','15时','16时','17时','18时','19时','20时','21时','22时','23时']
    }, {
        axisPointer: {
            show: false
        },
        axisLine: {
            lineStyle: {
                color: '#0E2A43'
            }
        },
        axisTick: {
            show: false
        },
        position: 'bottom',
        offset: 20
    }],
    yAxis: [{
        type: 'value',
        offset: 20,
        splitNumber:5,
       nameTextStyle:{fontSize:4},
        axisTick: {
            show: false
        },
        axisLine: {
            lineStyle: {
                color: '#0E2A43'
            }
        },
        axisLabel: {
            margin: 10,
            textStyle: {
                fontSize: 8,
                color: '#D5CBE8'
            }
        },
        splitLine: {
            show: false,
            lineStyle: {
                color: '#57617B'
            }
        }
    }],
    series: [{
        name: '',
        type: 'line',
        smooth: true,
        stack: '总量',
        symbol: 'circle',
        symbolSize: 5,
        showSymbol: false,
        animationDelay: 2000,
        animationDuration: 1000,
        markPoint: {
            // symbol: 'image://url',

            animationDelay: 3000,
            animationDuration: 1000
        },
        lineStyle: {
            normal: {
                width: 1,
                color: {
                    type: 'linear',
                    x: 0,
                    y: 0,
                    x2: 1,
                    y2: 0,
                    colorStops: [{
                        offset: 0, color: '#a4d8cc' // 0% 处的颜色
                    }, {
                        offset: 1, color: '#a4d8cc' // 100% 处的颜色
                    }],
                    globalCoord: true // 缺省为 false
                },
                opacity: 0.9
            }
        },
        areaStyle: {
            normal: {
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: 'rgba(137, 189, 27, 0.3)'
                }, {
                    offset: 0.8,
                    color: '#0e88c7'
                }], false),

            }
        },
        itemStyle: {
            normal: {
                color: '#7ec2ca',
                borderWidth: 3
            }
        },
        data: [710,312,321,754,500,830,710,521,504,660,530,420,710,312,321,754,500,830,710,521,504,660,530,410]
    }, ]
};
 myChart.setOption(optionfour);
       },
}
}
</script>

<style scoped>
  .conright {
    width: 23.4375%;
  }

  .ul-1 {
    border: 1px solid #01a2d8;
    position: relative;
    padding: 0;
    margin-left: 10px;
  }

  .ul-2 {
    border: 1px solid #01a2d8;
    position: relative;
    padding: 0;
    margin-left: 10px;
  }

  span {
    display: block;
    width: 10px;
    height: 10px;
    border: 2px solid #00fefa;
  }

  #t-left {
    border-right: none;
    border-bottom: none;
    position: absolute;
    left: -3px;
    top: -3px;
  }

  #t-right {
    border-left: none;
    border-bottom: none;
    position: absolute;
    right: -3px;
    top: -3px;
  }

  #b-left {
    border-top: none;
    border-right: none;
    position: absolute;
    left: -3px;
    bottom: -3px;
  }

  #b-right {
    border-top: none;
    border-left: none;
    position: absolute;
    right: -3px;
    bottom: -3px;
  }
</style>
