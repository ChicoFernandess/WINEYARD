<template>
  <div>
    <h1>MAPS WITH VUE</h1>
    <button @click="renderMap()">RENDER MAP</button>
    <div class="google-map" id="myMap"></div>
  </div>
</template>

<script>
export default {
  name: "Maps",
  data: function() {
    return {
      map: "",
      marker: "",
      infoWindow: "",
      contentString: "",
      lat: "",
      long: ""
    };
  },
  created: function() {
    if (localStorage.getItem("wineries")) {
      this.$store.state.wineries = JSON.parse(localStorage.getItem("wineries"));
    }
  },
  computed: {
    getSelectedRoute() {
      return this.$store.getters.routeSelect;
    }
  },
  methods: {
    renderMap() {
      if (this.getSelectedRoute == 1) {
        this.lat = 41.161933;
        this.long = -7.766806;
      } else if (this.getSelectedRoute == 2) {
        this.lat = 41.163577;
        this.long = -7.582799;
      } else if (this.getSelectedRoute == 3) {
        this.lat = 41.186872;
        this.long = -7.115952;
      }
      this.map = new google.maps.Map(document.querySelector("#myMap"), {
        center: { lat: this.lat, lng: this.long },
        zoom: 13,
        streetViewControl: false,
        scaleControl: false,
        zoomControl: true,
        mapTypeControl: false,
           styles: [
          
                   {
    elementType: "geometry",
    stylers: [
      {
        color: "#ebe3cd"
      }
    ]
  },
  {
    elementType: "labels",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#523735"
      }
    ]
  },
  {
    elementType: "labels.text.stroke",
    stylers: [
      {
        color: "#f5f1e6"
      }
    ]
  },
  {
    featureType: "administrative",
    elementType: "geometry",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "administrative",
    elementType: "geometry.stroke",
    stylers: [
      {
        color: "#c9b2a6"
      }
    ]
  },
  {
    featureType: "administrative.country",
    elementType: "geometry.fill",
    stylers: [
      {
        color: "#ffff00"
      },
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "administrative.land_parcel",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "administrative.land_parcel",
    elementType: "geometry.stroke",
    stylers: [
      {
        color: "#dcd2be"
      }
    ]
  },
  {
    featureType: "administrative.land_parcel",
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#ae9e90"
      }
    ]
  },
  {
    featureType: "administrative.neighborhood",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "landscape.natural",
    elementType: "geometry",
    stylers: [
      {
        color: "#dfd2ae"
      }
    ]
  },
  {
    featureType: "poi",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "poi",
    elementType: "geometry",
    stylers: [
      {
        color: "#dfd2ae"
      }
    ]
  },
  {
    featureType: "poi",
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#93817c"
      }
    ]
  },
  {
    featureType: "poi.park",
    elementType: "geometry.fill",
    stylers: [
      {
        color: "#a5b076"
      }
    ]
  },
  {
    featureType: "poi.park",
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#447530"
      }
    ]
  },
  {
    featureType: "road",
    elementType: "geometry",
    stylers: [
      {
        color: "#f5f1e6"
      }
    ]
  },
  {
    featureType: "road",
    elementType: "labels.icon",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "road.arterial",
    elementType: "geometry",
    stylers: [
      {
        color: "#fdfcf8"
      }
    ]
  },
  {
    featureType: "road.arterial",
    elementType: "geometry.fill",
    stylers: [
      {
        color: "#48464f"
      },
      {
        visibility: "on"
      },
      {
        weight: 2.5
      }
    ]
  },
  {
    featureType: "road.highway",
    elementType: "geometry",
    stylers: [
      {
        color: "#f8c967"
      }
    ]
  },
  {
    featureType: "road.highway",
    elementType: "geometry.fill",
    stylers: [
      {
        color: "#ffffff"
      },
      {
        weight: 2
      }
    ]
  },
  {
    featureType: "road.highway",
    elementType: "geometry.stroke",
    stylers: [
      {
        color: "#e9bc62"
      }
    ]
  },
  {
    featureType: "road.highway.controlled_access",
    elementType: "geometry",
    stylers: [
      {
        color: "#e98d58"
      }
    ]
  },
  {
    featureType: "road.highway.controlled_access",
    elementType: "geometry.stroke",
    stylers: [
      {
        color: "#db8555"
      }
    ]
  },
  {
    featureType: "road.local",
    elementType: "geometry.fill",
    stylers: [
      {
        visibility: "on"
      }
    ]
  },
  {
    featureType: "road.local",
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#806b63"
      }
    ]
  },
  {
    featureType: "transit",
    stylers: [
      {
        visibility: "off"
      }
    ]
  },
  {
    featureType: "transit.line",
    elementType: "geometry",
    stylers: [
      {
        color: "#dfd2ae"
      }
    ]
  },
  {
    featureType: "transit.line",
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#8f7d77"
      }
    ]
  },
  {
    featureType: "transit.line",
    elementType: "labels.text.stroke",
    stylers: [
      {
        color: "#ebe3cd"
      }
    ]
  },
  {
    featureType: "transit.station",
    elementType: "geometry",
    stylers: [
      {
        color: "#dfd2ae"
      }
    ]
  },
  {
    featureType: "water",
    elementType: "geometry.fill",
    stylers: [
      {
        color: "#b9d3c2"
      }
    ]
  },
  {
    featureType: "water",
    elementType: "labels.text.fill",
    stylers: [
      {
        color: "#92998d"
      }
    ]
  }
        ]
     
      });
      for (const winerie of this.$store.state.wineries) {
        if (winerie.route == this.getSelectedRoute) {
          this.marker = new google.maps.Marker({
            position: { lat: winerie.lat, lng: winerie.long },
            title: `${winerie.name}`,
            animation: google.maps.Animation.BOUNCE,
         icon: 'https://github.com/RuiFilipeSilva/WINEYARD/blob/master/src/assets/circulovermelho1.png?raw=true', // na net ver informacao de imagem e usar esse link 
   
          });
          this.contentString = `<div id="content"><div></div
          <h1 class="firstHeading">${winerie.name}</h1>
          <div><p>Latitude:${winerie.lat}</p>
          <p>Longitude:${winerie.long}</p>
          <button id=${winerie.id} @click="seleteWinerie(${winerie.id})">Ver Mais</button>
          </div></div>`;
          this.infoWindow = new google.maps.InfoWindow({
            content: this.contentString
          });
          this.marker.setMap(this.map);
          this.marker.addListener("click", () =>
            this.infowindow.open(this.map, this.marker)
          );
        }
      }
    },
    seleteWinerie(id) {
      this.$store.commit("SELECT_WINERIE", {
        idWinerie: id
      });
    }
  }
};
</script>
<style scoped>
.google-map {
  height: 500px;
  margin: 0 auto;
}
</style>