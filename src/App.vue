<template>
  <div id="app">
    <textarea name="name" rows="8" cols="80" v-model="joke"></textarea>
    <br>
    <button class="button" type="button" name="button" @click="getRandomJoke()">New</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      source: 'http://api.icndb.com/jokes',
      joke: ''
    }
  },
  created () {
    this.getRandomJoke()
  },
  methods: {
    getRandomJoke () {
      this.$http.get(this.source + '/random').then((response) => {
        let data = response.body
        if (data.type === 'success') {
          this.joke = data.value.joke
        }
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html {
  background: url('https://ugc.kn3.net/i/origin/http://www.wallpaper4me.com/images/wallpapers/Optimized-chucknorrisapproved-364971.jpeg') no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
}
.button {
    background-color: #4CAF50; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
}
</style>
