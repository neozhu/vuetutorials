<template>
  <div id="panorama"/>
</template>
<script>
import url_1 from "@/assets/01.jpeg";
import url_2 from "@/assets/02.jpeg";
export default {
  data: function() {
    return {};
  },
  methods: {
    createPannellum: function(tour) {
      const viewer = pannellum.viewer("panorama", {   
    "default": {
        "firstScene": "circle",
        "author": "昆山市",
        "sceneFadeDuration": 1000,
        "autoRotateInactivityDelay":2000,
        "autoLoad":true
    },
    
    "scenes": {
        "circle": {
            "title": "小区全景",
            "hfov": 110,
            "pitch": -3,
            "yaw": 117,
            "type": "equirectangular",
            "panorama": url_1,
            "hotSpots": [
                {
                    "pitch": -1.4476622300996986,
                    "yaw": -70.59580885187263,
                    "type": "scene",
                    "text": "往前走",
                    "sceneId": "house"
                },
                {
            "pitch": 5.4,
            "yaw": 110.8105838402667,
            "type": "info",
            "text": "这里是幼儿园"
        }
            ]
        },

        "house": {
            "title": "林荫小道",
            "hfov": 110,
            "yaw": 5,
            "type": "equirectangular",
            "panorama": url_2,
            "hotSpots": [
                {
                    "pitch": -1.5607644035618153,
                    "yaw": -123.98631107999095,
                    "type": "scene",
                    "text": "回去",
                    "sceneId": "circle",
                    "targetYaw": -23,
                    "targetPitch": 2
                },
                {
                    "pitch": 1.7,
                    "yaw": 2.0,
                    "type": "scene",
                    "text": "这是一颗大槐树",
                    "targetYaw": -23,
                    "targetPitch": 2
                }
            ]
        }
    }
});
      viewer.on("mousedown", function(e) {
        console.log("mousedown");
        console.log("Yaw " + viewer.getYaw());
        console.log("pitch " + viewer.getPitch());
        console.log(e);
      });
    }
  },
  mounted() {
    console.log(url_1);
    const tourjson = [{}];

    this.createPannellum(tourjson);
  }
};
</script>
<style>
.custom-hotspot {
  height: 50px;
  width: 50px;
  background: #f00;
}
div.custom-tooltip span {
  visibility: hidden;
  position: absolute;
  border-radius: 3px;
  background-color: #fff;
  color: #000;
  text-align: center;
  max-width: 200px;
  padding: 5px 10px;
  margin-left: -220px;
  cursor: default;
}
div.custom-tooltip:hover span {
  visibility: visible;
}
div.custom-tooltip:hover span:after {
  content: "";
  position: absolute;
  width: 0;
  height: 0;
  border-width: 10px;
  border-style: solid;
  border-color: #fff transparent transparent transparent;
  bottom: -20px;
  left: -10px;
  margin: 0 50%;
}
</style>