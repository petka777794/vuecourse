<template>
  <div class="home">
    <header-content></header-content>

    <main>
      <div class="banner">
        <div class="banner__content">
          <svg viewBox="0 0 220 80" preserveAspectRatio="xMidMid meet">
            <text x="110" y="77">Lorem ipsum dolor sit amet.</text>
          </svg>
          <p>Hotel - drinks - food - music</p>
          <div class="mouse"></div>
          <div class="newsletter-wrapper">
            <button class="icon-button">
              <i class="material-icons">mail_outline</i>
              <span class="outside-text">newsletter</span>
            </button>
          </div>
        </div>
      </div>

      <section-content title="EXCELLENCE AND QUALITY" subtitle="OASIS URBANO" class="articles-section">
        <div class="articles">
          <article-content title="Concept and phylosophy">
            <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fugit odit ea facilis quasi quis aliquam tempore consequuntur totam ducimus eligendi optio nisi provident aut laudantium deleniti maiores esse eius praesentium, velit nobis. Tempore deleniti quo itaque, commodi praesentium sint ipsam perspiciatis sunt possimus, hic nihil fuga repellat architecto, culpa obcaecati?</p>
          </article-content>

          <article-content title="Concept and phylosophy">
            <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fugit odit ea facilis quasi quis aliquam tempore consequuntur totam ducimus eligendi optio nisi provident aut laudantium deleniti maiores esse eius praesentium, velit nobis. Tempore deleniti quo itaque, commodi praesentium sint ipsam perspiciatis sunt possimus, hic nihil fuga repellat architecto, culpa obcaecati?</p>
          </article-content>
        </div>
        <link-button>know more</link-button>
      </section-content>

      <divider></divider>

      <section-content title="#Puroexperience" subtitle="featchured events">
        <carousel></carousel>
      </section-content>
    </main>

    <footer></footer>
  </div>
</template>

<script>
import HeaderContent from '@/components/HeaderContent';
import SectionContent from '@/components/SectionContent';
import ArticleContent from '@/components/ArticleContent';
import LinkButton from '@/components/LinkButton';
import Divider from '@/components/Divider';
import Carousel from '@/components/Carousel';

export default {
  name: 'home',

  data() {
    return {};
  },

  components: {
    HeaderContent,
    SectionContent,
    ArticleContent,
    LinkButton,
    Divider,
    Carousel,
  },
};
</script>

<style lang="scss">
.banner {
  min-height: 100vh;
  position: relative;

  display: flex;
  align-items: flex-end;
  box-sizing: border-box;
  justify-content: center;

  padding-bottom: 30px;

  background: {
    image: url('../assets/img/banner.jpg');
    size: cover;
    position: center;
    repeat: no-repeat;
    attachment: fixed;
  }

  &__content {
    display: flex;
    flex-direction: column;
    align-items: center;

    text-align: center;
    width: 100%;
    max-width: 500px;
  }

  h2 {
    margin: 0;

    font-size: 1.5em;
  }

  p {
    margin: 6px 0 24px 0;

    font-size: 0.7em;
  }

  h2,
  p {
    text-transform: uppercase;

    color: #fff;
  }

  svg {
    width: 100%;
    height: 100%;

    text-anchor: middle;

    text {
      font-size: 0.875em;
      fill: #fff;
    }
  }

  .mouse {
    display: none;

    position: relative;

    width: 24px;
    height: 42px;

    border: {
      width: 2px;
      style: solid;
      color: #fff;
      radius: 15px;
    }

    &:before {
      content: '';

      position: absolute;
      top: 20%;
      right: calc(50% - 3px);

      width: 6px;
      height: 6px;
      background-color: #fff;
      border-radius: 50%;

      animation: {
        name: mouse;
        duration: 1.2s;
        iteration-count: infinite;
      }
    }
  }

  .icon-button {
    width: 28px;
    height: 28px;
    box-sizing: border-box;

    position: relative;

    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    color: #fff;

    opacity: 0.7;

    cursor: pointer;

    border: {
      radius: 50%;
      width: 2px;
      color: #fff;
      style: solid;
    }

    i {
      font-size: 0.75em;
      margin-left: 1px;
    }

    &:focus,
    &:hover {
      .outside-text {
        right: 250%;
        opacity: 1;
      }
    }

    .outside-text {
      display: none;

      opacity: 0;
      position: absolute;
      right: 200%;

      font-size: 0.75em;

      text-transform: uppercase;

      transition: all 0.3s ease-in-out;

      &:after {
        content: '-';

        position: relative;
        left: 12px;
      }
    }
  }

  @media screen and (min-width: 900px) {
    .mouse {
      display: block;
    }

    .newsletter-wrapper {
      position: absolute;

      bottom: 30px;
      right: 30px;
    }

    .icon-button {
      .outside-text {
        display: block;
      }

      i {
        margin-left: 0;
      }
    }
  }
}

.articles{
  display: flex;
  flex-direction: column;
  margin-bottom: 24px;
}

@media screen and (min-width: 460px) {
  .articles{
    flex-direction: row;

    .article {
      &:not(:last-child) {
        margin-right: 24px;
      }
    }
  }
}

@media screen and (min-width: 460px) and (max-width: 900px) {
  .articles{
    flex-wrap: wrap;

    .article {
      width: 100%;
    }
  }
}

@media screen and (min-width: 1200px){
  .articles-section {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;

    & > div:first-child {
      width: calc(40% - 24px);
      margin-right: 24px;
    }

    .articles {
      width: 60%;
    }
  }
}
</style>
