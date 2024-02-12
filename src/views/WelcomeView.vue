
<template>
    <Header />
    <div class="w-full flex flex-wrap items-center justify-center sm:gap-16">
      <p class="custom-font-1 pl-4 sm:w-96">WELCOME TO GIPHY GALLERY!</p>
      <p class="custom-font-2 mt-5 sm:w-96 mb-5">
        Dive into the vast world of GIFs and discover an endless array of animated expressions to share with your friends and family. Whether you're looking for a hilarious moment, a heartfelt reaction, or a dose of nostalgia, we've got you covered.
      </p>
     
    </div>
  </template>
    
<script>
import Header from '@/components/Header.vue';



export default {
    name: 'WelcomeView',
    components: { Header }
}

</script>
  
<style scoped>
.custom-font-1 {
  font-family: 'Raleway', sans-serif;
  font-weight: 800;
    font-size: 4.5rem;
    background: linear-gradient(to right, yellow, red, purple, blue, rgb(51, 98, 51));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent; 
}

.custom-font-2 {
    font-family: 'Noto Sans', sans-serif;
    letter-spacing: 1px;
    font-weight: 300;
    line-height: 25px;
    color: #e2e2e2;
    font-size: 18px;
}

.welcome {
    width: 40rem;
    gap: 4rem;
    display: flex
}
</style>
  