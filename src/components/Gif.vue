<template>
   <div class="gif" :style="`background-image: url(${gif.images.original.url})`"></div>
</template>

<script>
export default {
    name: "Gif",
    props: {
        gif: Object
    }
}
</script>

<style scoped>
.gif {
  width: 240px;
  height: 240px;
  margin-bottom: 20px;
  display: inline-flex;
  justify-content: center;
  align-items: flex-end;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>