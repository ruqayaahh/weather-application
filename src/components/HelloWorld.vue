<template>
  <div class="hello">
    <div>
      <h1>{{ wel }}</h1>
      <h3>{{ msg }}</h3>
    </div>
    <div>
      <form action="" @submit.prevent="$emit('getReport', cityname)">
        <label for="">
          <input type="text" v-model="cityname" placeholder="where are you?" />
          <button>Weather report</button>
        </label>
      </form>
    </div>

    <div>
      <div>
        <ul>
          <li>Location: {{ city }}</li>
          <br />
          <li>Temperature: {{ temp }} degree Celsius</li>
          <br />
          <li>Weather Summary: {{ weather }}</li>
          <br />
          <li>Current Weather Description: {{ description }}</li>
          <br />
        </ul>
      </div>

      <div v-if="showImage">
        <div v-show="!hot">
          <img src="../assets/cold.jpg" alt="" />
        </div>
        <div v-show="hot">
          <img src="../assets/hot.png" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    wel: String,
    msg: String,
    info: Object,
    city: String,
    temp: Number,
    weather: String,
    description: String,
    showImage: Boolean,
    hot: Boolean,
  },
  data() {
    return {
      cityname: "",
    };
  },
};
</script>

<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
