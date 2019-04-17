<template>
  <div class="nav-links">
    <a href="/" v-on:click="toggleArchive">Home</a>
    <a href="/images" v-on:click="toggleArchive">Images Archive</a>
  </div>
</template>

<script>
export default {
  name: "Nav",
  props: {
    toggleArchive: Function
  }
};
</script>

<style scope>
.nav-links a {
  margin: 10px;
  font-size: 1.5rem;
  text-decoration: none;
  color: rgb(133, 133, 133)
}
.nav-links a:hover {
  color: rgb(106, 153, 169);
}
</style>