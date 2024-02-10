
<template>
  <search @fetch-gifs="onFetch"/>
  <gif-list :gifs="gifs"/>
</template>
  
<script>
  import Search from '@/components/Search.vue';
  import GifList from '@/components/GifList.vue';
  export default {
    name: 'App',
    components: {
      GifList,
      Search
    },
    data() {
      return {
        gifs: [],
      }
    }, 
    methods: {
      onFetch(result) {
        this.gifs = result;
      }

    },
}

</script>

<style scoped>
* {
  box-sizing: border-box;
}
body {
  padding: 50px
}

#app {
  width: 800px;
  margin: 0 auto;
}
</style>
