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
      chart: null
    }
  },
  mounted() {
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
        title: {
          text: '我的活动任务进度',
          textStyle: {
            color: '#333',
            fontSize: 14
          },
          left: 10
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: { // 坐标轴指示器，坐标轴触发有效
            type: 'shadow' // 默认为直线，可选为：'line' | 'shadow'
          }
        },
        grid: {
          top: 40,
          left: '2%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [{
          type: 'value',
          axisTick: {
            show: false,
            alignWithLabel: true
          },
          axisLine: {
            lineStyle: {
              color: '#ddd'
            }
          },
          axisLabel: {
            textStyle: {
              color: '#333'
            }
          }
        }],
        yAxis: [{
          type: 'category',
          nameTextStyle: {
            color: 'red'
          },
          axisTick: {
            show: false
          },
          data: ['投票', '沙龙', '随堂小测', '调查问卷', '在线测试', '课程作业'],
          axisLine: {
            lineStyle: {
              color: '#ddd'
            }
          },
          axisLabel: {
            textStyle: {
              color: '#333'
            }
          }
        }],
        series: [{
          name: 'studentA',
          type: 'bar',
          stack: 'vistors',
          barWidth: '50%',
          label: {
            normal: {
                show: true,
                position: 'right',
                color: '#333',
                formatter: '{c}%'
            }
          },
          data: ['20', '5', '33', '70', '52', '95'],
          animationDuration,
          itemStyle: {
            color: '#FF8C00',
            shadowColor: 'rgba(0, 0, 0, 0.5)',
            shadowBlur: 10,
            shadowOffsetX: 0,
            shadowOffsetY: 6
          }
        }]
      })
    }
  }
}
</script>
