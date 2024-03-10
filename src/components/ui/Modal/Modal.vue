<script setup>
defineProps({
  isOpen: Boolean,
  closeModal: Function
});
</script>

<template>
  <transition name="modal">
    <div class="modal_wrapper" v-if="isOpen">
      <div class="modal">
        <button @click="closeModal">
          <img src="/close_modal.svg" alt="" />
        </button>
        <slot />
      </div>
    </div>
  </transition>
</template>

<style lang="scss" scoped>
.modal-enter-active,
.modal-leave-active {
  transition: all 0.5s ease;

  .modal,
  .modal_wrapper {
    transition: all 0.5s ease;
  }
}

.modal-enter-from,
.modal-leave-to {
  .modal_wrapper {
    opacity: 0;
  }
  .modal {
    transform: translateY(200px);
    opacity: 0;
  }
}

.modal_wrapper {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 50;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #57a03cc9;
}

.modal {
  min-width: 1000px;
  min-height: 600px;
  border-radius: 50px;
  background: white;
  position: relative;
  padding: 30px;
  button {
    background: none;
    border: none;
    width: 30px;
    height: 30px;
    cursor: pointer;

    img {
      width: 30px;
      height: 30px;
      transition: all 0.1s ease-in;
      position: absolute;
      right: 30px;
      top: 30px;
    }

    &:hover {
      img {
        transform: rotate(180deg) scale(1.2);
      }
    }
  }
}
</style>
