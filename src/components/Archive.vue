<template>
  <div>
    <h3>Archives</h3>
    <div class="thumb">
      <div v-for="archive in archives" class="pic">
        <img :src="archive.url" alt>
        {{archive.date}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Archive",
  props: {
    archives: Array
  }
};
</script>

<style scope>
.thumb {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.thumb img {
  max-width: 200px;
}
.pic {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 10px;
}
</style>