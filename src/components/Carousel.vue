<template>
  <div class="carousel">
    <button type="button" @click="slideLeft">
      <i class="material-icons">chevron_left</i>
    </button>
      <ul :style="{width: `${carouselWidth}px`, transform: `translateX(${translate}px)`}">
        <carousel-item :key="index" v-for="(slide, index) in slides"
        :title="slide.title"
        :subtitle="slide.subtitle"
        :cost="slide.cost"
        :style="{width: `${carouselItemWidth}px`}"></carousel-item>
    </ul>
    <button type="button" @click="slideRight">
      <i class="material-icons">chevron_right</i>
    </button>
  </div>
</template>

<script>
import CarouselItem from '@/components/CarouselItem';

export default {
  name: 'caroursel',

  components: {
    CarouselItem,
  },

  data() {
    const slides = [
      {
        title: 'Title 1',
        subtitle: 'Subtitle 1',
        cost: '14',
      },
      {
        title: 'Title 2',
        subtitle: 'Subtitle',
      },
      {
        title: 'Title 3',
        subtitle: 'Subtitle 3',
        cost: '58',
      },
      {
        title: 'Title 4',
        subtitle: 'Subtitle 444',
        cost: '',
      },
      {
        title: 'Title ',
        subtitle: 'Subtitle ',
        cost: '77',
      },
    ];
    const horizontalPadding = 22 * 2;
    const itemsMargins = 4 * 16;
    const carouselItemWidth =
      (window.innerWidth - horizontalPadding - itemsMargins) / 4;
    const slidesMargins = 16 * slides.length;
    const carouselWidth = carouselItemWidth * slides.length;

    return {
      carouselWidth: carouselWidth + slidesMargins,
      carouselItemWidth,
      slides,
      translate: 0,
    };
  },

  mounted() {
    window.addEventListener('resize', this.handleResize);
  },

  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize);
  },

  methods: {
    handleResize() {
      const horizontalPadding = 22 * 2;
      const itemsMargins = 4 * 16;
      this.carouselItemWidth =
        (window.innerWidth - horizontalPadding - itemsMargins) / 4;
      const slidesMargins = 16 * this.slides.length;
      const carouselWidth = this.carouselItemWidth * this.slides.length;

      this.carouselWidth = carouselWidth + slidesMargins;
    },
    slideLeft() {
      this.translate += this.carouselItemWidth + 16;
    },
    slideRight() {
      this.translate -= this.carouselItemWidth + 16;
    },
  },
};
</script>

<style lang="scss">
.carousel {
  position: relative;
  overflow: hidden;

  ul {
    height: 400px;
    margin: 0 -8px;
    overflow: hidden;

    transition: all 0.3s ease-in-out;

    li {
      &:nth-child(1) .slide__content {
        background-image: url(../assets/img/slides/slide-1.jpg);
      }

      &:nth-child(2) .slide__content {
        background-image: url(../assets/img/slides/slide-2.jpg);
      }

      &:nth-child(3) .slide__content {
        background-image: url(../assets/img/slides/slide-3.jpg);
      }

      &:nth-child(4) .slide__content {
        background-image: url(../assets/img/slides/slide-4.jpg);
      }
    }
  }

  button {
    position: absolute;
    background-color: #fff;
    width: 16px;
    height: 32px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    top: calc(50% - 60px);

    z-index: 1;

    i {
      display: flex;
      position: relative;
      justify-content: center;
      font-size: 20px;
      width: 16px;
    }

    &:first-child {
      left: 0;

      border-top-right-radius: 32px;
      border-bottom-right-radius: 32px;

      i {
        left: -2px;
      }
    }

    &:last-child {
      right: 0;

      border-top-left-radius: 32px;
      border-bottom-left-radius: 32px;

      i {
        right: -2px;
      }
    }
  }
}
</style>
