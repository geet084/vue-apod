<template>
  <div id="app">
    <Nav :toggleArchive="this.toggleArchive"/>
    <Archive v-if="this.showArchives" :archives="this.archives"/>
    <Display v-else :apodImage="this.apodImage"/>
  </div>
</template>

<script>
import Display from "./components/Display.vue";
import Nav from "./components/Nav.vue";
import Archive from "./components/Archive.vue";

export default {
  name: "app",
  created: function() {
    this.fetchPic(), this.fetchAllPics(), this.toggleArchive();
  },
  data() {
    return {
      apodImage: {},
      archives: [],
      showArchives: false
    };
  },
  components: {
    Display,
    Nav,
    Archive
  },
  methods: {
    fetchPic: function() {
      const root = 'https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY'
      
      this.$http.get(root).then(result => {
        this.apodImage = result.data;
      });
    },
    fetchAllPics: function() {
      let newDate = new Date();
      let date = newDate.toDateString().split(" ");
      let months = ["none", "Jan", "Feb", "Mar", "Apr", "May"];
      let currDay = parseInt(date[2]);

      for (let i = 1; i < currDay + 1; i++) {
        let day = i < 10 ? `0${i}` : i;
        let specificDay =
          "&date=" + date[3] + "-0" + months.indexOf(date[1]) + "-" + day;
        const root = `https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY${specificDay}`
        this.$http.get(root).then(result => {
          this.archives = [...this.archives, result.data];
        });
      }
    },
    toggleArchive: function(e) {
      e.preventDefault();
      this.showArchives = !this.showArchives;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #567da5;
  margin-top: 60px;
}
body {
  background-color: rgb(36, 36, 36);
}
</style>
