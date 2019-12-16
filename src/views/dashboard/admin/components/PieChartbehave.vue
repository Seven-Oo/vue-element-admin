<template>
  <div :class="className" :style="{height:height,width:width}" />
</template>

<script>
import echarts from 'echarts'
require('echarts/theme/macarons') // echarts theme
import resize from './mixins/resize'

const animationDuration = 6000

export default {
  mixins: [resize],
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '380px'
    }
  },
  data() {
    return {
      chart: null,
      pieData: [
        {
          name: '装备制造',
          value: 54
        },{
            name: '现代材料',
            value: 44
        },{
            name: '新能源',
            value: 35
        },{
            name: '新一代信息技术',
            value: 30
        },{
            name: '商贸物流',
            value: 20
        }
      ],
      pietitleArr: [], 
      pieseriesArr: [],
      pieColors: [
        ['#389af4', '#dfeaff'],
        ['#ff8c37', '#ffdcc3'],
        ['#ffc257', '#ffedcc'], 
        ['#fd6f97', '#fed4e0'],
        ['#a181fc', '#e3d9fe']
      ]
    }
  },
  mounted() {
    var self = this;
    this.pieData.forEach(function(item, index){
        self.pietitleArr.push(
            {
                text:item.name,
                left: index * 20 + 10 +'%',
                top: '65%',
                textAlign: 'center',
                textStyle: {
                    fontWeight: 'normal',
                    fontSize: '16',
                    color: self.pieColors[index][0],
                    textAlign: 'center',
                },
            }        
        );
        self.pieseriesArr.push(
            {
                name: item.name,
                type: 'pie',
                clockWise: false,
                radius: [60, 70],
                itemStyle:  {
                    normal: {
                        color: self.pieColors[index][0],
                        shadowColor: self.pieColors[index][0],
                        shadowBlur: 0,
                        label: {
                            show: false
                        },
                        labelLine: {
                            show: false
                        },
                    }
                },
                hoverAnimation: false,
                center: [index * 20 + 10 +'%', '50%'],
                data: [{
                    value: item.value,
                    label: {
                        normal: {
                            formatter: function(params){
                                return params.value+'%';
                            },
                            position: 'center',
                            show: true,
                            textStyle: {
                                fontSize: '20',
                                fontWeight: 'bold',
                                color: self.pieColors[index][0]
                            }
                        }
                    },
                }, {
                    value: 100-item.value,
                    name: 'invisible',
                    itemStyle: {
                        normal: {
                            color: self.pieColors[index][1]
                        },
                        emphasis: {
                            color: self.pieColors[index][1]
                        }
                    }
                }]
            }    
        )
    })

    this.$nextTick(() => {
      this.initChart()
    })
  },
  beforeDestroy() {
    if (!this.chart) {
      return
    }
    this.chart.dispose()
    this.chart = null
  },
  methods: {
    initChart() {
      this.chart = echarts.init(this.$el, 'macarons')

      this.chart.setOption({
        backgroundColor: "#fff",
        title: this.pietitleArr,
        series: this.pieseriesArr
      })
    }
  }
}
</script>