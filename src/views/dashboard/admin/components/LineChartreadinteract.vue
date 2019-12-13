<template>
  <div :class="className" :style="{height:height,width:width}" />
</template>

<script>
import echarts from 'echarts'
require('echarts/theme/macarons') // echarts theme
import resize from './mixins/resize'

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
    },
    autoResize: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {

    }
  },

  mounted() {
    this.$nextTick(() => {
      this.initChart()
    })
  },
  methods: {
    initChart() {
      this.chart = echarts.init(this.$el, 'macarons')
      this.setOptions()
    },
    setOptions({ } = {}) {
      this.chart.setOption({
        title: {
          text: '我的阅读总次数VS我的互动总次数',
          textStyle: {
            color: '#333',
            fontSize: 14
          },
          left: 10
        },
        xAxis: {
          data: ['12月9日', '12月10日', '12月11日', '12月12日', '12月13日', '12月14日', '12月15日'],
          boundaryGap: false,
          axisTick: {
            show: false
          }
        },
        yAxis: {
          type: 'value',
          data: [0, 50, 100, 150, 200],
          axisTick: {
            show: false
          }
        },
        grid: {
          left: 10,
          right: 40,
          bottom: 50,
          top: 40,
          containLabel: true
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross'
          },
          padding: [5, 10]
        },

        legend: {
          data: ['我的阅读总次数', '我的互动总次数'],
          bottom: 10
        },
        series: [{
          name: '我的阅读总次数',
          smooth: true,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#3888fa',
              lineStyle: {
                color: '#3888fa',
                width: 2
              },
              areaStyle: {
                color: '#fff'
              }
            }
          },
          smooth: false,
          type: 'line',
          data: [39, 54, 13, 79, 123, 25, 90],
          animationDuration: 2800,
          animationEasing: 'cubicInOut'
        },
        {
          name: '我的互动总次数',
          smooth: false,
          type: 'line',
          itemStyle: {
            normal: {
              color: '#FF8C00',
              lineStyle: {
                color: '#FF8C00',
                width: 2
              },
              areaStyle: {
                color: '#fff'
              }
            }
          },
          data: [0, 82, 91, 154, 162, 140, 145],
          animationDuration: 2800,
          animationEasing: 'quadraticOut'
        }]
      })
    }
  }
}
</script>
