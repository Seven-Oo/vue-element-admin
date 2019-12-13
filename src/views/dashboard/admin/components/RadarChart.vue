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
            text: '我的互动',
            textStyle: {
              color: '#333', //标题颜色
              fontSize: 14
            }
        },
        grid: {
          left: '10%'
        },
        tooltip: {},
        legend: {
          icon: 'rect',
	        right : '5%', 
          itemWidth: 20,                  
          itemHeight: 4,  
          orient: 'vertical',
          textStyle: {                   
            fontSize: 12,
            color: '#333'
	        },
          data: ['我的互动总次数', '平均互动总次数', '最高互动总次数']
        },
        radar: {
          name: {
            textStyle: {
              color: '#333',
              borderRadius: 3,
              padding: [0, 0]
            }
          },
          center: ['50%','54%'],//调整雷达图的位置
          radius: 110,//半径，可放大放小雷达图
          indicator: [
            {name: '发帖', max: 100},
            {name: '回文', max: 100},
            {name: '点赞+获得点赞', max: 100},
            {name: '沙龙发言', max: 100},
            {name: '抢答', max: 100},
            {name: '提问', max: 100},
            {name: '问卷+投票', max: 100}
          ]
        },
        series: [{
          name: '我的互动总次数',
          type: 'radar',
          itemStyel: {
            borderWidth: 0
          },
          lineStyle: {
            color: '#3888fa',
            width: 3
          },
          areaStyle: {
            color: 'transparent'
          },
          data: [
              {name: "我的互动总次数", value: [10, 44, 65, 81, 3, 66, 24]}
          ]
        },
        {
          name: '平均互动总次数',
          type: 'radar',
          lineStyle: {
            color: '#FF8C00',
            width: 3
          },
          areaStyle: {
            color: 'transparent'
          },
          data: [
              {name: "能力值", value: [3, 51, 37, 85, 90, 12, 48]}
          ]
        },
        {
          name: '最高互动总次数',
          type: 'radar',
          lineStyle: {
            color: '#D3D3D3',
            width: 3
          },
          areaStyle: {
            color: 'transparent'
          },
          data: [
              {name: "能力值", value: [97, 23, 7, 83, 67, 44, 29]}
          ]
        }]
      })
    }
  }
}

</script>