<template>
    <div 
        class="catalog" 
        v-if="open" 
        v-bind:style="{ height: `calc(100vh - ${headerHeight}px)` }"
    >
        <div class="catalog__inner">
            <div class="catalog__sidebar">
                Sidebar
            </div>
            <div class="catalog__categories">
                Categories
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Catalog',
  props: {
    open: Boolean,
  },
  data() {
    return {
        headerHeight: 0,
    }
  },

  mounted() {
    const header = document.querySelector('.header');
    this.headerHeight = header.clientHeight;
  },
}
</script>

<style lang="scss">
.catalog {
    width: 100%;
    position: sticky;
    top: 0;
    height: 100vh;

    &__inner {
        @include container;
        display: flex;
    }

    &__sidebar {
        width: 328px;
        padding: 40px 0;
        margin-right: 40px;
    }

    &__categories {
        padding: 40px 0;
        border-left: $primary-border;
    }
}
</style>