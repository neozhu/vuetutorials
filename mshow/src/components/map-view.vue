<template>
  <v-container class="ma-0 pa-0" style="width: 100%;height: 100%">
    <v-layout text-xs-center wrap style="width: 100%;height: 100%">
      <v-flex xs12 style="width: 100%;height: 100%">
        <div class="m-map" style="width: 100%;height: 100%">
              <div id="js-container" class="map" style="width: 100%;height: 100%">正在加载数据 ...</div>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import { MapCityName,Location } from '@/config/config'
export default {
 
  data () {
    return {
      AMapUI: null,
      AMap: null
    }
  },
  watch: {
    
  },
  methods: {
    
    // 实例化地图
    initMap () {
      // 加载PositionPicker，loadUI的路径参数为模块名中 'ui/' 之后的部分
     
      let that =this;
      let AMapUI = this.AMapUI = window.AMapUI
      let AMap = this.AMap = window.AMap
      AMapUI.loadUI(['misc/PositionPicker'], PositionPicker => {
        let mapConfig = {
          zoom: 14,
          cityName: MapCityName
        }
        if (Location) {
          mapConfig.center = [Location.lng, Location.lat]
        }
        let map = new AMap.Map('js-container', mapConfig)
        
        // 启用工具条
        AMap.plugin(['AMap.ToolBar'], function () {
          map.addControl(new AMap.ToolBar({
            position: 'RB'
          }))
        })
        //添加一个marker
        var marker = new AMap.Marker({
          icon: "https://webapi.amap.com/theme/v1.3/markers/n/mark_b.png",
          position: [Location.lng, Location.lat],
          title: '小区全景'
         });
         map.add(marker);
         marker.on('click', function(){
            //这里我需要路由到其它页面，但怎么做都是错误，因为没办法调用$router
             that.$router.push('about');
         });
      });
      
    },
    toPreview () {
      this.$router.push('about');
    }
  },
  async created () {
    // 已载入高德地图API，则直接初始化地图
    
    if (window.AMap && window.AMapUI) {
      this.initMap()
    // 未载入高德地图API，则先载入API再初始化
    }  
  }
}
</script>

<style>
</style>
