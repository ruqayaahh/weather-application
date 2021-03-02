<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld
      :wel="wel"
      :msg="msg"
      @getReport="weatherData"
      :info="info"
      :city="city"
      :temp="temp"
      :weather="weather"
      :description="description"
      :showImage="showImage"
      :hot="hot"
    />
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      wel: "Welcome to Our Weather Report Platform",
      msg: "Check weather report of your current location",
      info: {},
      city: "",
      kelvin: 0,
      temp: 0,
      weather: "",
      description: "",
      showImage: false,
      hot: false,
    };
  },
  methods: {
    weatherData(cityname) {
      this.showImage = false;
      const api = "https://api.openweathermap.org/data/2.5/weather?q=";
      let city = cityname;
      const apiKey = "&appid=9678383e74cdb44e52cba56dcb3621d0";
      let apiURL = api + city + apiKey;

      fetch(apiURL)
        .then((response) => response.json())
        .then((data) => {
          this.info = data;
          this.city = city;
          this.kelvin = this.info.main.temp;
          this.temp = Math.round(this.kelvin - 273);
          this.weather = this.info.weather[0].main;
          this.description = this.info.weather[0].description;
          if (this.temp < 23) {
            return (this.hot = false);
          } else {
            return (this.hot = true);
          }
        })
        .catch((error) => alert(error))
        .finally(() => (this.showImage = true));
    },
  },
};
</script>
