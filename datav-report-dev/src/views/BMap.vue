<template>
  <v-chart :option="options" />
</template>

<script>
import 'echarts/extension/bmap/bmap'
const testPoint = [{
  name: '海门',
  value: [121.15, 31.89, 80]
}, {
  name: '南京',
  value: [118.78, 32.04, 100]
}]
const testPoint2 = [{
  name: '北京',
  value: [116.40, 39.91, 200]
}, {
  name: '上海',
  value: [121.48, 31.22, 195]
}]
  export default {
    data() {
      return {
        options: {}
      }
    },
    mounted() {
      /* eslint-disable */
      this.options = {
        title: {
          text: '外卖数据大盘',
          subtext: '趋势统计',
          sublink: 'https://www.baidu.com/'
        },
        bmap: {
          key: 'G1LFyjrNGIkns5OfpZnrCGAKxpycPLwb',
          center: [104.114129, 37.550339],
          zoom: 5, // 缩放比例
          roam: true, // 是否允许缩放
          mapStyle: {
            // 自定义地图Json
            styleJson: [{
                'featureType': 'water',
                'elementType': 'all',
                'stylers': {
                  'color': '#d1d1d1'
                }
              }, {
                'featureType': 'land',
                'elementType': 'all',
                'stylers': {
                  'color': '#f3f3f3'
                }
              }, {
                'featureType': 'railway',
                'elementType': 'all',
                'stylers': {
                  'visibility': 'off'
                }
              }, {
                'featureType': 'highway',
                'elementType': 'all',
                'stylers': {
                  'color': '#fdfdfd'
                }
              }, {
                'featureType': 'highway',
                'elementType': 'labels',
                'stylers': {
                  'visibility': 'off'
                }
              }, {
                'featureType': 'arterial',
                'elementType': 'geometry',
                'stylers': {
                  'color': '#fefefe'
                }
              }, {
                'featureType': 'arterial',
                'elementType': 'geometry.fill',
                'stylers': {
                  'color': '#fefefe'
                }
              }, {
                'featureType': 'poi',
                'elementType': 'all',
                'stylers': {
                  'visibility': 'off'
                }
              }, {
                'featureType': 'green',
                'elementType': 'all',
                'stylers': {
                  'visibility': 'off'
                }
              }, {
                'featureType': 'subway',
                'elementType': 'all',
                'stylers': {
                  'visibility': 'off'
                }
              }, {
                'featureType': 'manmade',
                'elementType': 'all',
                'stylers': {
                  'color': '#d1d1d1'
                }
              }, {
                'featureType': 'local',
                'elementType': 'all',
                'stylers': {
                  'color': '#d1d1d1'
                }
              }, {
                'featureType': 'arterial',
                'elementType': 'labels',
                'stylers': {
                  'visibility': 'off'
                }
              }, {
                'featureType': 'boundary',
                'elementType': 'all',
                'stylers': {
                  'color': '#fefefe'
                }
              }, {
                'featureType': 'building',
                'elementType': 'all',
                'stylers': {
                  'color': '#d1d1d1'
                }
              }, {
                'featureType': 'label',
                'elementType': 'labels.text.fill',
                'stylers': {
                  'color': '#999999'
                }
              }]
          }
        },
        tooltip: {},
        series: [{
          name: 'sales',
          type: 'scatter', // 散点图
          coordinateSystem: 'bmap', // 坐标系统
          data: testPoint, // 数据源
          encode: {
            value: 2 // 散点 强调使用的数据 这里的 value: 2 表示 value: testPoint[i].value[2]
          },
          itemStyle: {
            color: 'red' // 三点颜色
          },
          symbolSize: function(val) {
            return val[2] / 10 // 散点图大小
          },
          label: {
            show: false, // 是否显示标签
            position: 'right', // 标签显示位置
            formatter: function(v) {
              return `${v.data.name} - ${v.data.value[2]}`
            }
          },
          emphasis: {
            // 强调 交互功能 鼠标移上去时
            label: {
              show: true // 显示标签
            }
          }
        }, {
          name: 'Top 2',
          type: 'effectScatter',
          coordinateSystem: 'bmap', // 坐标系统
          data: testPoint2, // 数据源
          encode: {
            value: 2 // 散点 强调使用的数据 这里的 value: 2 表示 value: testPoint[i].value[2]
          },
          symbolSize: function(val) {
            return val[2] / 10 // 散点图大小
          },
          label: {
            show: false, // 是否显示标签
            position: 'right', // 标签显示位置
            formatter: function(v) {
              return `${v.data.name} - ${v.data.value[2]}`
            }
          },
          emphasis: {
            // 强调 交互功能 鼠标移上去时
            label: {
              show: true // 显示标签
            }
          },
          hoverAnimate: true,
          rippleEffect: {
            brushType: 'stroke' // 水波纹图
          },
          itemStyle: {
            color: 'gold', 
            shadowblur: 10, // 阴影
            shadowColor: 'blue' // 阴影色
          }
        }]
      }
    }
  }
</script>

<style lang="scss" scoped>
</style>
