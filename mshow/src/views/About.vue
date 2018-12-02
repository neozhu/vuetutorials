<template>

  <div id="panorama"/>
</template>
<script>
import url_1 from "@/assets/02.jpeg"
export default {
		data: function() {
			return {
				
			}
		},
		methods: {
			createPannellum: function(tour) {
				const viewer = pannellum.viewer('panorama', {
   "type": "equirectangular",
    "panorama": url_1,
		"autoLoad":true,
		"compass":true,
		"autoRotate": -2,
		"hotSpots": [
        
				{
            "pitch": -11.02,
            "yaw": -133.83356429361672,
            "type": "info",
            "text": "Art Museum Drive"
        },
        

					],
		"mousedown":function(e){ console.log(e)}
});
      viewer.on('mousedown',
    function (e) {
        console.log("mousedown");
				console.log("Yaw " + viewer.getYaw());
				console.log("pitch " + viewer.getPitch());
				console.log(e);
    }
);
			}
		},
		mounted() {
			console.log(url_1)
      const tourjson=[{}];
      
			this.createPannellum(tourjson)
		}
	}
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
    div.custom-tooltip:hover span{
        visibility: visible;
    }
    div.custom-tooltip:hover span:after {
        content: '';
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