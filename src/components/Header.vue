<template>
  <header class="header">
    <Topline />

    <div class="header__inner">
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

      <Search />

      <AccountLinks />
    </div>

    <Catalog :open="isOpen" />
  </header>
</template>

<script>
import Topline from "./Topline.vue";
import Search from "./Search.vue";
import AccountLinks from './AccountLinks.vue';
import Catalog from './Catalog.vue';

import Logo from '@/assets/logo.svg';

export default {
  name: 'Header',
  components: {
    Topline,
    Search,
    AccountLinks,
    Catalog
  },
  data() {
    return {
      isOpen: false,
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
    }
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
    border-bottom: $primary-border;
  }

  &__logo {
    margin-right: 45px;
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
    display: flex;
    align-items: center;
    gap: 20px;

    &--open {
      background-image: url('@/assets/catalog-close.svg');
    }
  }
}
</style>
