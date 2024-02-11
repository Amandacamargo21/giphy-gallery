
<template>
  <section class="p-10">
    <div v-if="isLoading" class="flex justify-center items-center h-screen">
      <div class="loader ease-linear rounded-full border-4 border-t-4 border-gray-200 h-12 w-12 mb-4"></div>
    </div>
    <search @fetch-gifs="onFetch" @empty-input="searchInitialGifs"/>
    <gif-list v-if="!isLoading" :gifs="gifs"/>
  </section>
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
        offset: 0,
        limit: 15,
        isLoading: false,
      }
    }, 
    mounted() {
    this.searchInitialGifs();
    window.addEventListener('scroll', this.onScroll);
  },
    methods: {
      searchInitialGifs() {
      this.isLoading = true; 
      setTimeout(() => {
      this.searchGifs();
      }, 500); 
    },
    searchGifs() {
      this.isLoading = true;
      fetch(`https://api.giphy.com/v1/gifs/trending?api_key=MOazGpFAidHLr2nDYwcGjAc7LrlRJiUg&offset=${this.offset}&limit=${this.limit}`)
        .then(response => response.json())
        .then(result => {
          console.log(result);
          this.gifs = this.gifs.concat(result.data); 
          this.offset += this.limit; 
          this.isLoading = false;
        })
        .catch(error => {
          console.error('Error fetching data:', error);
          this.isLoading = false; 
        });
    },
    onScroll() {
      if ((window.innerHeight + window.scrollY) >= document.body.offsetHeight) {
        this.searchGifs();
      }
    },
    onFetch(result) {
        this.gifs = result;
      }
  }
}
</script>

<style scoped>
.loader {
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #1a202c;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
