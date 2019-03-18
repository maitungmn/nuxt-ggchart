<template>
  <div id="map"></div>
</template>

<style>
  /* Always set the map height explicitly to define the size of the div
   * element that contains the map. */
  #map {
    height: 100%;
  }

  /* Optional: Makes the sample page fill the window. */
  html, body {
    height: 100%;
    margin: 0;
    padding: 0;
  }
</style>

<script>
  import google from '@/assets/google-map'

  export default {
    created() {
      let tokyo = {lat: 35.652832, lng: 139.839478};

      let map = new google.maps.Map(document.getElementById('map'), {
        scaleControl: true,
        center: tokyo,
        zoom: 10
      });

      let infowindow = new google.maps.InfoWindow;
      infowindow.setContent('<b>tokyo</b>');

      let marker = new google.maps.Marker({map: map, position: tokyo});
      marker.addListener('click', function () {
        infowindow.open(map, marker);
      });
    }
  }
</script>
