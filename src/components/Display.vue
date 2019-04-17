<template>
  <div>
    <h1>NASA Astronomy Picture of the Day</h1>
    <h2>{{apodImage.title}}</h2>
    <div>
      <img :src="apodImage.url" alt>
      <p class="explanation">{{apodImage.explanation}}</p>
      <p class="footer">Date: {{apodImage.date}} Copyright: {{apodImage.copyright}}</p>
    </div>
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
  font-size: 2.4rem;
  background-color: rgb(0, 0, 0);
  color: rgb(106, 153, 169);
}
h2 {
  margin: 15px auto -52px;
  font-size: 2.4rem;
  width: 900px;
  border-radius: 10px;
}
h2, p {
  background-color: rgb(143, 143, 143);
  color: black;
  position: relative;
}
.explanation {
  padding: 15px;
  margin: 0 auto;
  bottom: 265px;
  width: 900px;
  border-radius: 15px;
}
.footer {
  padding: 5px 15px;
  bottom: 255px;
  width: 400px;
  margin: 0 auto;
  border-radius: 8px;
}
</style>
