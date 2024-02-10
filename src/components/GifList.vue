<template>
  <div class="gifList">
    <gif v-for="gif in gifs" :key="gif.id" :gif="gif"/>
  </div>
</template>

<script>
import Gif from "@/components/Gif.vue";
export default {
    name: "GifList",
    components: {Gif},
    props: {
        gifs: Array
    }
}
</script>

<style scoped>
  #gifList {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
</style>