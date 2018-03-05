<template>
  <div id="app">
    <textarea name="name" rows="8" cols="80" v-model="joke"></textarea>
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
</style>
