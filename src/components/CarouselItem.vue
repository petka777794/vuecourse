<template>
  <li class="slide">
    <div class="slide__content">
      <div class="slide__backdrop">
        <h3 class="slide__title">{{title}}</h3>
        <p class="slide__subtitle">{{subtitle}}</p>
        <div class="slide__cost">{{getCost()}}</div>
      </div>
    </div>
    <div class="slide__bottom-area">
      <link-button>know more</link-button>
    </div>
  </li>
</template>

<script>
import LinkButton from '@/components/LinkButton';

export default {
  name: 'caroursel-item',

  props: ['title', 'subtitle', 'cost'],

  components: {
    LinkButton,
  },

  methods: {
    getCost() {
      return this.cost && `$${this.cost}`;
    },
  },
};
</script>

<style lang="scss">
.slide {
  position: relative;

  float: left;

  margin: 0 8px;

  &:hover {
    .slide__bottom-area {
      transform: translateY(0);
      opacity: 1;
    }
  }

  &__content {
    box-sizing: border-box;

    background: {
      image: url(../assets/img/valentiensolofondo.jpg);
      size: cover;
      position: center;
    }
  }

  &__backdrop {
    padding: 16px;
    height: 300px;
    box-sizing: border-box;

    background-color: rgba(0, 0, 0, 0.3);
  }

  &__title,
  &__subtitle,
  &__cost {
    color: #fff;

    margin-top: 0;
  }

  &__title {
    font-size: 1.5em;
    margin-bottom: 8px;
  }

  &__cost {
    display: inline-block;

    font-size: 2em;
    font-weight: bold;

    padding-top: 16px;
    border-top: 1px solid #fff;
  }

  &__bottom-area {
    margin-top: 16px;

    text-align: center;

    transform: translateY(-16px);
    transition: all 0.4s ease-in-out;
    opacity: 0;
  }
}
</style>
