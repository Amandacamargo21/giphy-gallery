<template>
  <div>
    <div class="gif" 
      :style="`background-image: url(${gif.images.original.url})`"
      @click="showModal = true">
    </div>
    <transition name="fade">
      <div v-if="showModal" class="modal-overlay" @click="closeModal">
        <div class="modal">
          <button @click="closeModal" class="close-button">
            <span aria-hidden="true">&times;</span>
          </button>
          <img :src="gif.images.original.url" class="gif-image" alt="gif">
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Gif",
  props: {
    gif: Object
  },
  data() {
    return {
      showModal: false
    };
  },
  methods: {
    closeModal() {
      this.showModal = false;
    }
  }
}
</script>

<style scoped>
.gif {
  width: 200px;
  height: 200px;
  background-size: cover;
  position: relative;
}

.gif:hover {
  cursor: pointer;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}

.modal {
  background-color: white;
  padding: 60px 20px 20px; 
  border-radius: 5px;
  position: relative;
}

.gif-image {
  max-width: 100%;
  max-height: calc(80vh - 60px); 
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to{
  opacity: 0;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 24px;
  color: #000;
  cursor: pointer;
}
</style>
