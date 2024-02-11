<template>
  <div class="gifList">
    <gif v-for="gif in gifs" :key="gif.id" :gif="gif" :class="{ 'expanded': gif.isExpanded }"
      @close-gif="closeGif(gif)" />
  </div>
</template>

<script>
import Gif from "@/components/Gif.vue";
import ShareButtons from "@/components/ShareButtons.vue";

export default {
  name: "GifList",
  components: {
    Gif,
    ShareButtons
  },
  props: {
    gifs: Array
  },
  methods: {
    closeGif(gif) {
      gif.isExpanded = false;
    }
  }
}
</script>

<style scoped>
.gifList {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding-top: 1rem;
  justify-content: center;
}

.gif {
  width: 200px;
  height: 200px;
  background-size: cover;
  position: relative;
}

.gif:hover {
  cursor: pointer;
}

.gif.expanded {
  width: 400px;
  height: 400px;
}

.gif img {
  width: 100%;
  height: 100%;
}
</style>
