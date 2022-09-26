<template>
    <div 
        class="mobile-menu"
        v-if="open"
        :class="{'mobile-menu--open': open}"
    >
        <Topline class="mobile-menu__topline" />
    </div>
</template>

<script>
import Topline from "./Topline.vue";

export default {
    name: 'Catalog',
    components: {
    Topline,
    },
    props: {
    open: Boolean,
    },
}
</script>

<style lang="scss">
.mobile-menu {
    position: absolute;
    top: 0;
    left: 0;
    width: 80%;
    height: 100vh;
    background-color: #fff;
    z-index: 2;
    border-right: $primary-border;

    &__topline {
        & .topline__inner {
            flex-wrap: wrap;
            flex-direction: column;
        }

        & .topline__contact {
            justify-content: flex-start;
        }

        & .topline__list {
            flex-wrap: wrap;
            flex-direction: column;
        }
    }

}
</style>