<template>
  <div class="app-wrapper app-padded-vertical">
    <h2 class="app-subtitle">Location</h2>
    <p class="app-description">
      {{ home.location.address }} {{ home.location.city }}
      {{ home.location.state }} {{ home.location.country }}
    </p>
    <div class="app-map" ref="map"></div>
  </div>
</template>

<script>
export default {
  props: {
    home: {
      type: Object,
      required: true,
    },
  },

  mounted() {
    this.$maps.showMap({
      canvas: this.$refs.map,
      lng: this.home._geoloc.lng,
      lat: this.home._geoloc.lat,
    });
  },
};
</script>