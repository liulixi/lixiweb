<template>
  <div class="Echarts">
    <div id="main" style="width: 600px;height:600px;"></div>
  </div>
</template>

<script>
import world from '../../assets/js/world.js'

export default {
  name: "Echarts",
  methods: {
    myEcharts() {
      var dom = document.getElementById("main");
      var myChart = this.$echarts.init(dom);

      // 使用 echarts 绘制世界地图的实例作为纹理
      var canvas = document.createElement("canvas");
      var texture = this.$echarts.init(canvas, null, {
        width: 4096,
        height: 2048,
      });

      texture.setOption({
        backgroundColor: "#dddee0",
        geo: [
          {
            //type: 'map',
            map: "world",
            top: 0,
            left: 0,
            right: 0,
            bottom: 0,
            silent: true, //图形是否不响应和触发鼠标事件
            boundingCoords: [
              [-180, 90],
              [180, -90],
            ]
          }
        ],
        series: [
          {
            name: "地点", // series名称
            type: "effectScatter", // series图表类型
            coordinateSystem: "geo", // series坐标系类型
            color: "red",
            rippleEffect: {
              period: "3",
              scale: "5",
              brushType: "stroke",
            },
            data: [{ name: "重庆", value: [106.33, 29.35, 90] }],
          },
        ]
      });

      var option = {
        globe: {
          show: true,
          baseTexture: texture,
          shading: "color",
          viewControl: {
            rotateSensitivity: 3, //鼠标旋转灵敏度，设置为0后无法旋转。
            zoomSensitivity: 0, //鼠标缩放灵敏度
            autoRotate: true, //自动旋转
            autoRotateAfterStill: 1, //鼠标停止后多久恢复旋转(为0时暂停后不恢复旋转)
            targetCoord: [116.46, 39.92], //定位到哪里
          },
        },

        series: {
          type: "scatter3D",
          cursor:'default',
          coordinateSystem: "globe",
          blendMode: "lighter",
          symbolSize: 2,
          itemStyle: {
            color: "rgb(50, 50, 150)",
            opacity: 0.2,
          },
          data: [10, 100, 100, 200],
        },
      };
      myChart.setOption(option);
    },
  },
  mounted() {
    this.myEcharts();
  },
};
</script>

<style>
</style>
