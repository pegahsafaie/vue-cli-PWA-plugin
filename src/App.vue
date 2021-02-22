<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <label for="lname">Your ip:</label>
    <input type="text" v-model="ip" />
    <button type="button" @click="apiCall">Show Country</button>
    <button type="button" @click="reset">Reset</button>
    <span>{{address}}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      ip:'8.8.8.8',
      address:'',
    }
  },
  methods: {
    reset() {
      this.address = '';
    },
    apiCall() {
      console.log(this.ip);
      fetch(`https://get.geojs.io/v1/ip/country.json?ip=${this.ip}`)
      .then(response => response.json())
      .then(data => {
        this.address = data[0].name;
      });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
