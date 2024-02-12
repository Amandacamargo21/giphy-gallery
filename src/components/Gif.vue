<template>
  <div>
    <div class="gif" :style="`background-image: url(${gif.images.original.url})`" @click="showModal = true"
      @mouseenter="hovering = true" @mouseleave="hovering = false">
      <div v-if="hovering" class="overlay" :class="{ 'overlay-visible': hovering }"></div>
    </div>
    <transition name="fade">
      <div v-if="showModal" class="modal-overlay" @click="closeModal">
        <div class="modal">
          <div class="flex justify-between items-center pb-4 border-b-2 border-solid border-gray-300">
            <p class="text-2xl">Share this gif!</p>
            <button @click="closeModal" class="close-button">
              <span aria-hidden="true">
                <font-awesome-icon icon="xmark" />
              </span>
            </button>
          </div>
          <img :src="gif.images.original.url" class="gif-image" alt="gif">
          <ShareButtons />
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import ShareButtons from "@/components/ShareButtons.vue";

export default {
  name: "Gif",
  components: {
    ShareButtons
  },
  props: {
    gif: Object
  },
  data() {
    return {
      showModal: false,
      hovering: false,
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
  border-radius: 10px;
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
  padding: 1.5rem;
  border-radius: 5px;
  position: relative;
}

.gif-image {
  max-width: 100%;
  max-height: calc(80vh - 60px);
  border-radius: 10px;
  margin-top: 1rem;
  position: relative;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.close-button {
  /* position: absolute; */
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 24px;
  color: #000;
  cursor: pointer;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0);
  transition: background-color 0.5s ease-in-out;
  border-radius: 10px;
}

.overlay-visible {
  background-color: rgba(0, 0, 0, 0.5);
}
</style>
