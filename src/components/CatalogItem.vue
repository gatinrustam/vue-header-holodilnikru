<template>
    <div class="catalog-item">
        <h3 class="catalog-item__title">{{catalog[activeId].title}}</h3>

        <div class="catalog-item__list">
            {{activeId}}
        </div>
    </div>
</template>

<script>
import catalogData from '@/db/catalog.json';

export default {
    name: "CatalogItem",
    props: {
        activeId: Number,
    },
    data() {
        return {
            catalog: catalogData,
        };
    },
}
</script>

<style lang="scss">
.catalog-item {
    width: 100%;
    flex: 1 0 auto;
    margin-right: 40px;

    &__list {
        display: flex;
        flex-wrap: wrap;
        margin-bottom: 40px;
    }

    &__title {
        margin-bottom: 24px;
        font-weight: 700;
        font-size: 24px;
        line-height: 32px;
    }
}
</style>