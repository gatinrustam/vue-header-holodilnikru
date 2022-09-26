<template>
  <header class="header">
    <Topline class="header__topline" />

    <div class="header__inner">
      <div 
        class="header__menu"
        @click="showMenu()"
      ></div>

      <a href="#" class="header__logo">
        <img :src="Logo" alt="logo" />
      </a>

      <button 
        type="button" 
        class="header__catalog"
        :class="{'header__catalog--open': isOpen}"
        @click="showCatalog()"
      >
        <span>Каталог</span>
      </button>

      <Search class="header__search" />

      <AccountLinks class="header__account" />
    </div>

    <Search class="header__search-mobile" />
    <Catalog class="header__catalog-menu" :open="isOpen" />
    <MobileMenu :open="isOpenMenu" />
  </header>
</template>

<script>
import Topline from "./Topline.vue";
import Search from "./Search.vue";
import AccountLinks from './AccountLinks.vue';
import Catalog from './Catalog.vue';
import MobileMenu from './MobileMenu.vue';

import Logo from '@/assets/logo.svg';

export default {
  name: 'Header',
  components: {
    Topline,
    Search,
    AccountLinks,
    Catalog,
    MobileMenu
  },
  data() {
    return {
      isOpen: false,
      isOpenMenu: false,
    }
  },
  setup() {
    return {
      Logo,
    };
  },
  methods: {
    showCatalog() {
      this.isOpen = !this.isOpen;

      document.body.style.overflow = this.isOpen ? 'hidden' : '';
    },
    showMenu() {
      this.isOpenMenu = !this.isOpenMenu;
    },
  },
}
</script>

<style scoped lang="scss">
.header {
  position: relative;
  
  &__inner {
    @include container;
    padding-top: 20px;
    padding-bottom: 20px;
    display: flex;
    align-items: center;
    border-bottom: $primary-border;

    @media screen and (max-width: $max-mobile) {
      justify-content: space-between;
      align-items: center;
    }
  }

  &__logo {
    margin-right: 45px;
    height: 45px;

    @media screen and (max-width: $max-mobile) {
    margin-right: 0;
    }
  }

  &__catalog {
    background-image: url('@/assets/catalog-open.svg');
    background-position: 24px center;
    background-repeat: no-repeat;
    background-color: $primary-blue;
    color: #fff;
    outline: none;
    border-radius: 6px;
    border: none;
    padding: 10px 24px 10px 64px;
    font-size: 18px;
    cursor: pointer;
    height: 45px;
    transition: $transition;

    &:hover {
      background-color: $primary-blue-hover;
    }

    @media screen and (max-width: $max-mobile) {
      display: none;
    }

    &--open {
      background-image: url('@/assets/catalog-close.svg');
    }
  }

  &__search-mobile {
    display: none;
  }

  @media screen and (max-width: $max-mobile) {
    &__search {
      display: none;
    }

    &__account {
      flex: 0 0 auto;
    } 

    &__search-mobile {
      display: block;
      max-width: none;
      margin: 24px auto;
      padding: 0 16px;
    }

    &__topline {
      display: none;
    }

    &__catalog-menu {
      display: none;
    }

  }

  &__menu {
    width: 32px;
    height: 32px;
    background-image: url('@/assets/menu.svg');
    background-repeat: no-repeat;
    background-size: 100%;
    display: none;
    cursor: pointer;
    z-index: 10;

    @media screen and (max-width: $max-mobile) {
      display: block;
    }
  }
  
}
</style>
