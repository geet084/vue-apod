<template>
  <div id="app">
    <Display :apodImage="this.apodImage"/>
  </div>
</template>

<script>
import Display from './components/Display.vue'

export default {
  name: 'app',
  created: function () {
    this.fetchPic()
  },
  data () {
    return {
      apodImage: {}
    }
  },
  components: {
    Display
  },
  methods: {
    fetchPic: function () {
      const root = 'https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY'
      this.$http.get(root)
      .then(result => {
        console.log(result.data)
        this.apodImage = result.data
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
