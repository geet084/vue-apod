<template>
  <div>
    <h1>Nasa APoD</h1>
    <p>{{apodImage.explanation}}</p>
    <img :src="apodImage.url" alt="">
  </div>
</template>

<script>
export default {
  name: "Display",
  props: {
    apodImage: Object
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 40px 0 0;
}
</style>
