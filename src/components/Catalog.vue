<template>
    <div 
        class="catalog" 
        v-if="open"
    >
        <div class="catalog__inner">
            <div class="catalog__sidebar">
                <div 
                    class="catalog__item catalog__item--popular"
                    @mouseover="activeMenu = null"
                >
                    <span class="catalog__icon catalog__icon--popular"></span>
                    <span>Популярные бренды</span>
                </div>

                <div 
                    v-for="(item, index) in catalogMenu"
                    :key="item.id"
                    @mouseover="activeMenu = index"
                    class="catalog__item"
                >
                    <span 
                        class="catalog__icon" 
                        :class="[item.icon ? 'catalog__icon--' + item.icon : '']"
                    ></span>
                    {{item.title}}
                </div>

                <div class="catalog__item catalog__item--stock">
                    <span class="catalog__icon catalog__icon--stock"></span>
                    Акции
                </div>
                <div class="catalog__item catalog__item--sales">
                    <span class="catalog__icon catalog__icon--sales"></span>
                    Распродажа
                </div>
                <div class="catalog__item catalog__item--discounted">
                    <span class="catalog__icon catalog__icon--discounted"></span>
                    Уцененные товары
                </div>
            </div>
            <div class="catalog__categories">
                <CatalogItem 
                    v-if="activeMenu !== null" 
                    :activeId="activeMenu" 
                />
                <PopularBrands v-else />
            </div>
        </div>
    </div>
</template>

<script>
import CatalogItem from '@/components/CatalogItem.vue';

import catalogData from '@/db/catalog.json';
import PopularBrands from './PopularBrands.vue';

export default {
    name: "Catalog",
    components: {
        PopularBrands,
        CatalogItem,
    },
    props: {
        open: Boolean,
    },
    data() {
        return {
            headerHeight: 0,
            catalogMenu: catalogData,
            activeMenu: null,
        };
    },
    mounted() {
        const header = document.querySelector(".header");
        this.headerHeight = header.clientHeight;
    },
}
</script>

<style lang="scss">
.catalog {
    width: 100%;
    height: 100vh;

    &__inner {
        @include container;
        display: flex;
    }

    &__sidebar {
        width: 100%;
        min-width: 328px;
        height: calc(100vh - 214px);
        margin: 40px 40px 40px 0;
        overflow-x: hidden;
        overflow-y: scroll;
        flex-grow: 0;
        flex-shrink: 1;
        flex-basis: 0%;

        &::-webkit-scrollbar {
            width: 6px;
        }

        &::-webkit-scrollbar-track {
            background-color: $primary-gray-bg;
            border-radius: 10px;
        }

        &::-webkit-scrollbar-thumb {
            background-color: $primary-blue;
            border-radius: 10px;
        }
    }

    &__categories {
        height: calc(100vh - 214px);
        width: 100%;
        margin: 40px 40px 40px 0;
        padding-left: 40px;
        overflow-x: hidden;
        overflow-y: scroll;
        border-left: $primary-border;

        &::-webkit-scrollbar {
            width: 6px;
        }

        &::-webkit-scrollbar-track {
            background-color: $primary-gray-bg;
            border-radius: 10px;
        }

        &::-webkit-scrollbar-thumb {
            background-color: $primary-blue;
            border-radius: 10px;
        }
    }

    &__item {
        color: $text-color;
        font-size: 18px;
        line-height: 24px;
        padding: 10px 8px;
        border-radius: 6px;
        margin-right: 40px;
        display: flex;
        align-items: center;
        gap: 8px;
        cursor: pointer;
        transition: $transition;

        &:hover {
            background-color: $primary-gray-bg;
        }

        &--popular {
            border-bottom: $primary-border;
        }

        &--stock {
            border-top: $primary-border;
        }
    }

    &__icon {
        width: 24px;
        height: 24px;
        display: inline-block;
        background-size: cover;

        &--popular {
            background-image: url('@/assets/icons/popular.svg');
        }
        &--smartphone {
            background-image: url('@/assets/icons/smartphone.svg');
        }
        &--tv {
            background-image: url('@/assets/icons/tv.svg');
        }
        &--audio {
            background-image: url('@/assets/icons/audio.svg');
        }
        &--computers {
            background-image: url('@/assets/icons/computers.svg');
        }
        &--ref {
            background-image: url('@/assets/icons/ref.svg');
        }
        &--wash {
            background-image: url('@/assets/icons/wash.svg');
        }
        &--embedded {
            background-image: url('@/assets/icons/embedded.svg');
        }
        &--diswash {
            background-image: url('@/assets/icons/diswash.svg');
        }
        &--stove {
            background-image: url('@/assets/icons/stove.svg');
        }
        &--kitchen {
            background-image: url('@/assets/icons/kitchen.svg');
        }
        &--home {
            background-image: url('@/assets/icons/home.svg');
        }
        &--beauty {
            background-image: url('@/assets/icons/beauty.svg');
        }
        &--air {
            background-image: url('@/assets/icons/air.svg');
        }
        &--repair {
            background-image: url('@/assets/icons/repair.svg');
        }
        &--sport {
            background-image: url('@/assets/icons/sport.svg');
        }
        &--kids {
            background-image: url('@/assets/icons/kids.svg');
        }
        &--garden {
            background-image: url('@/assets/icons/garden.svg');
        }
        &--smart {
            background-image: url('@/assets/icons/smart.svg');
        }
        &--stock {
            background-image: url('@/assets/stock.svg');
        }
        &--sales {
            background-image: url('@/assets/sales.svg');
        }
        &--discounted {
            background-image: url('@/assets/discounted.svg');
        }
    }
}
</style>