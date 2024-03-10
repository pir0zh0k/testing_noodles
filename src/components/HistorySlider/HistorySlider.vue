<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import { FreeMode } from 'swiper/modules';
import Modal from '@/components/ui/Modal/Modal.vue';
import 'swiper/css';
import { ref } from 'vue';
import { SLIDER_DATA } from './slider.data';

export default {
  components: {
    Swiper,
    SwiperSlide,
    Modal
  },
  setup() {
    const modalIsOpen = ref(false);

    function openModal() {
      modalIsOpen.value = true;
    }

    function closeModal() {
      modalIsOpen.value = false;
    }

    return {
      SLIDER_DATA,
      modalIsOpen,
      openModal,
      closeModal,
      modules: [FreeMode]
    };
  }
};
</script>

<template>
  <Modal :isOpen="modalIsOpen" :close-modal="closeModal">
    <div class="modal_title">
      <h1>1999</h1>
      <img src="/modal_arrow.svg" alt="" />
      <p>Первая пачка<br />вермишели</p>
    </div>
    <img class="title_line" src="/modal_line.svg" />
    <img class="modal_image" src="/modal_image.png" />
    <img src="/leaf.png" alt="" class="leaf" />
    <img src="/tomato.png" alt="" class="tomato" />
    <p class="modal_content">
      «Роллтон» – это любимые продукты миллионов потребителей. А всё потому, что вкус и качество
      ароматной кудрявой лапши и неповторимого нежного пюре остаются неизменными на протяжении
      более, чем 20 лет.
    </p>
    <p class="modal_content">
      «Роллтон» объединяет всех, независимо от пола и возраста, и всегда выручает горячим обедом!
      Где бы вас не настиг голод: на работе, в поездке или дома, ваш сытный перекус — всегда
      под рукой.
    </p>
  </Modal>
  <div class="history_slider">
    <div class="__container history_container">
      <h1 class="history_title">
        <span>История</span>
        Роллтон
      </h1>
    </div>
    <div class="__container">
      <Swiper :slides-per-view="3" :freeMode="true">
        <SwiperSlide v-for="slide in SLIDER_DATA" :key="slide.id">
          <div class="slide" @click="openModal">
            <img class="product" :src="slide.image" alt="" />
            <div class="content">
              <h1>{{ slide.date }}</h1>
              <p v-html="slide.text"></p>
            </div>
          </div>
          <img class="slider_connect_line" :src="slide.connect_line" />
        </SwiperSlide>
      </Swiper>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.modal_content {
  max-width: 430px;
  margin-top: 50px;
  color: #5f5f5f;
  font-size: 18px;
  line-height: 140%;

  &:last-child {
    margin-top: 20px;
  }
}
.leaf {
  position: absolute;
  right: 370px;
  top: 70px;
  z-index: 50;
}
.tomato {
  position: absolute;
  right: 60px;
  bottom: 70px;
  z-index: 50;
}
.modal_image {
  position: absolute;
  z-index: 30;
  width: 490px;
  right: 20px;
  bottom: 0;
}

.title_line {
  position: absolute;
  right: 0;
  top: 160px;
  width: 80%;
}

.modal_title {
  display: flex;
  align-items: center;
  gap: 20px;

  h1 {
    font-weight: 700;
    font-size: 62px;
    color: #fbd927;
  }

  p {
    font-weight: 500;
    line-height: 25px;
    font-size: 24px;
  }

  img {
    width: 100px;
  }
}

.history_slider {
  position: relative;
  z-index: 10;
  width: 100%;
  height: 100%;
  background-color: #fffbde;
}

.history_container {
  padding-top: 100px;
  margin-bottom: 80px;
}

.history_title {
  text-transform: uppercase;
  font-weight: 700;
  font-size: 35px;
  color: #fbd927;

  span {
    color: #e13320;
  }
}

.slider_connect_line {
  position: absolute;
  width: 250px;
  right: -100px;
  top: 230px;
  pointer-events: none;
}

.slide {
  width: 500px;
  height: 470px;
  position: relative;
  z-index: 5;
  background-image: url('/slider_circle.svg');
  background-repeat: no-repeat;
  background-position: 70px 70px;
  cursor: pointer;

  .content {
    position: absolute;
    right: 100px;
    bottom: 0;

    h1 {
      font-weight: 700;
      font-size: 62px;
      color: #fbd927;
    }

    p {
      font-weight: 500;
      line-height: 20px;
    }
  }

  .product {
    position: absolute;
    top: 10px;
    left: 15px;
    transition: all 0.5s ease;
  }

  &:hover {
    background-image: url('/slider_circle_opened.svg');

    .product {
      transform: rotate(5deg);
      scale: 1.1;
    }
  }
}
</style>
