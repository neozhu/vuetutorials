<template>
  <div id="panorama"/>
</template>
<script>
export default {
		data: function() {
			return {
				
			}
		},
		methods: {
			createPannellum: function(tour) {
				const view= pannellum.viewer('panorama', {
   "type": "equirectangular",
    "panorama": "https://pannellum.org/images/jfk.jpg",
    "autoRotate": -2
});
			}
		},
		mounted() {
      const tourjson=[{}];
      
			this.createPannellum(tourjson)
		}
	}
</script>