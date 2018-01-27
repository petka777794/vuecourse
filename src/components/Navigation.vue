<template>
  <nav>
    <button class="open-button material-icons" aria-label="open menu" @click="toggleNavigation(true)">menu</button>

    <transition name="fade">
      <div class="mobile-menu" v-if="open">
        <Trap :disabled="!open">
          <button class="close-button material-icon" aria-label="close menu" @click="toggleNavigation(false)">close</button>
          <navigation-menu></navigation-menu>
        </Trap>
      </div>
    </transition>

    <navigation-menu></navigation-menu>
  </nav>
</template>


<script>
import Trap from 'vue-focus-lock';
import NavigationMenu from '@/components/NavigationMenu';

export default {
  name: 'navigation',

  data() {
    return {
      open: false,
      windowWidth: window.innerWidth,
    };
  },

  components: {
    Trap,
    NavigationMenu,
  },

  methods: {
    toggleNavigation(state) {
      this.open = state;

      document.body.style.overflow = state ? 'hidden' : 'auto';
    },
  },
};
</script>

<style lang="scss">
nav {
  position: absolute;
  right: 20px;
  top: 22px;

  .open-button.material-icons {
    font-size: 2em;
    cursor: pointer;
    color: #fff;

    transition: all .3s ease-in-out;

    &:hover,
    &:focus {
      color: #97623f;
    }

    &:focus {
      outline: none;
    }
  }

  .mobile-menu {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

    padding: 50px;

    background-color: #fff;

    .close-button {
      position: absolute;
      top: 21.5px;
      right: 20px;
    }

    ul {
      li {
        &:not(:last-child) {
          margin-bottom: 16px;
        }
        a {
          text-decoration: none;
          color: #333;
          font-size: 1.8em;

          &:hover,
          &:focus {
            outline: none;
          }
        }
      }
    }
  }

  & > ul {
    display: none;
    flex-direction: row;
    padding-top: 6px;

    li {
      &:not(:last-child) {
        margin-bottom: 16px;
        margin-right: 25px;
      }

      a {
        text-transform: uppercase;
        text-decoration: none;
        color: #fff;
        font-size: 0.875em;

        &:hover {
          color: #97623f;
        }

        &:focus {
          outline: none;
        }
      }
    }
  }

  @media screen and (min-width: 900px) {
    position: static;

    .open-button {
      display: none;
    }

    & > ul {
      display: flex;
    }
  }
}
</style>
