<script setup>
import gsap from 'gsap';
import { ref } from 'vue';

const closedNoodleRef = ref(null);
const openedNoodleRef = ref(null);
const arrowRef = ref(null);
const logoRef = ref(null);
const bottomArrowRef = ref(null);
const confettiRef = ref(null);
const bluredConfettiRef = ref(null);
const yearsRef = ref(null);

const toggleNoodles = () => {
  gsap.fromTo(
    logoRef.value,
    {
      width: '100%'
    },
    {
      position: 'absolute',
      width: 242,
      left: 20,
      top: 0
    }
  );

  gsap.fromTo(
    arrowRef.value,
    {
      opacity: 1
    },
    {
      opacity: 0,
      duration: 1
    }
  );

  gsap.fromTo(
    closedNoodleRef.value,
    {
      opacity: 1
    },
    {
      opacity: 0,
      duration: 1
    }
  );
  gsap.fromTo(
    openedNoodleRef.value,
    {
      opacity: 0
    },
    {
      opacity: 1,
      duration: 1
    }
  );
  gsap.fromTo(
    bottomArrowRef.value,
    {
      opacity: 0
    },
    {
      opacity: 1,
      duration: 1
    }
  );

  gsap.fromTo(
    confettiRef.value,
    { opacity: 0, y: 300, scale: 0 },
    {
      opacity: 1,
      y: 0,
      scale: 1,
      delay: 0.5
    }
  );

  gsap.fromTo(
    bluredConfettiRef.value,
    { opacity: 0, y: 300, scale: 0 },
    {
      opacity: 1,
      y: 0,
      scale: 1,
      delay: 0.5
    }
  );

  gsap.fromTo(
    yearsRef.value,
    { opacity: 0, y: 300 },
    {
      opacity: 1,
      y: 0,
      delay: 1
    }
  );
};
</script>

<template>
  <div class="preview_screen">
    <div class="__container preview_container">
      <img ref="logoRef" class="logo" src="/logo.svg" alt="" />
      <div class="ellipse"></div>
      <div class="open_me" ref="arrowRef">
        <span>Открой меня</span>
        <img src="/preview_arrow.svg" alt="" />
      </div>
      <img
        @click="toggleNoodles"
        ref="closedNoodleRef"
        class="closed_noodles"
        src="/collage_1.png"
        alt=""
      />
      <img ref="confettiRef" class="confetti" src="/confetti.svg" alt="" />
      <img ref="bluredConfettiRef" class="blured_confetti" src="/blured_confetti.svg" alt="" />
      <img ref="yearsRef" class="years" src="/25_years.svg" alt="" />
      <img ref="openedNoodleRef" class="opened_noodles" src="/collage_2.png" alt="" />
      <img ref="bottomArrowRef" class="bottom_arrow" src="/bottom_arrow.svg" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.preview_screen {
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: #df231d;
}

.preview_container {
  padding: 0 36px;
  position: relative;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;

  .years {
    position: absolute;
    z-index: 7;
    bottom: 90px;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
    pointer-events: none;
  }

  .confetti {
    position: absolute;
    z-index: 5;
    bottom: 130px;
    opacity: 0;
    pointer-events: none;
  }
  .blured_confetti {
    position: absolute;
    z-index: 5;
    bottom: 240px;
    left: 80px;
    opacity: 0;
    pointer-events: none;
  }

  .bottom_arrow {
    opacity: 0;
    position: absolute;
    z-index: 10;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
    animation-name: bottom_arrow_shake;
    animation-duration: 0.5s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
    pointer-events: none;
  }

  .ellipse {
    position: absolute;
    bottom: -50%;
    background-color: #ffde32;
    width: 800px;
    height: 1000px;
    border-radius: 50%;
    filter: blur(150px);
  }

  .logo {
    display: block;
    position: relative;
    z-index: 3;
    margin-top: 63px;
    width: 100%;
  }

  .opened_noodles {
    position: absolute;
    width: 60%;
    bottom: -20px;
    left: 50%;
    transform: translateX(-55%);
    opacity: 0;
  }

  .closed_noodles {
    position: absolute;
    width: 60%;
    bottom: -20px;
    left: 50%;
    transform-origin: 10% 50%;
    transform: translateX(-55%);
    animation-name: rotation;
    animation-duration: 1.2s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
    z-index: 3;

    &:hover {
      cursor: pointer;
      animation-name: drag;
      animation-duration: 0.2s;
      animation-iteration-count: infinite;
      animation-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
    }
  }
}

.open_me {
  position: absolute;
  z-index: 5;
  left: 30%;
  top: 70%;
  pointer-events: none;

  img {
    width: 200px;
    animation-name: spin;
    animation-duration: 1s;
    animation-iteration-count: infinite;
  }

  span {
    position: absolute;
    top: 25px;
    left: -20px;
    color: #df231d;
    font-weight: 600;
    font-size: 18px;
  }
}

@keyframes bottom_arrow_shake {
  0% {
    bottom: 10px;
  }

  50% {
    bottom: 0;
  }

  100% {
    bottom: 10px;
  }
}

@keyframes spin {
  0% {
    transform: rotate(10deg);
  }
  50% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(10deg);
  }
}

@keyframes rotation {
  0% {
    transform: rotate(3deg) translateX(-55%);
  }

  50% {
    transform: rotate(0deg) translateX(-55%);
  }

  100% {
    transform: rotate(3deg) translateX(-55%);
  }
}

@keyframes drag {
  0% {
    transform: translateX(-56%);
  }

  50% {
    transform: translateX(-54%);
  }

  100% {
    transform: translateX(-56%);
  }
}
</style>
