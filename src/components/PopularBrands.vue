<template>
    <div class="popular-brands">
        <h3 class="popular-brands__title">Популярные бренды</h3>

        <div class="popular-brands__list">
            <div 
                class="popular-brands__item"
                v-for="item in popular"
            >
                <span 
                    v-if="item.logo" 
                    :class="['popular-brands__logo', 'popular-brands__logo--' + item.logo]"
                ></span>
                <div class="popular-brands__desc">
                    {{item.description}}
                </div>
                <a 
                    class="popular-brands__link"
                    :href="item.url"
                >Каталог "{{item.title}}"</a>
            </div>
        </div>

        <ul class="popular-brands__all">
            <li 
                class="popular-brands__all-item" 
                v-for="(brand, index) in addLetter()"
                :key="brand.id"
            >
                <span 
                    class="popular-brands__all-letter"
                    v-if="brand.hasLetter"
                >
                    {{
                        brand.hasLetter
                    }}
                </span>
                <a :href="brand.url" class="popular-brands__all-link">{{brand.title}}</a>
            </li>
        </ul>
    </div>
</template>

<script>
import popularData from '@/db/popular-brands.json';
import allBrandsData from '@/db/all-brands.json';

export default {
    name: "PopularBrands",
    data() {
        return {
            popular: popularData,
            all: allBrandsData,
        };
    },
    methods: {
        addLetter() {
            const listWithLetter = Array.from(this.all); // immutable
            
            for (let i = 0; i < listWithLetter.length; i++){
                listWithLetter[i].hasLetter = listWithLetter[i].title[0];
                
                if (i !== 0 && listWithLetter[i].title[0] === listWithLetter[i - 1].title[0]) {
                    listWithLetter[i].hasLetter = '';
                }
            }
            return listWithLetter;
        }
    },
}
</script>

<style lang="scss">
.popular-brands {
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

    &__item {
        width: 30%;
        margin-right: 30px;
        margin-bottom: 24px;
    }

    &__desc {
        color: $text-color-light;
        font-size: 14px;
        line-height: 20px;
        margin-bottom: 8px;
    }

    &__link {
        color: $text-color-links;
        font-size: 14px;
        line-height: 20px;
        text-decoration: none;
    }

    &__logo {
        display: block;
        height: 40px;
        width: 90px;
        background-repeat: no-repeat;
        background-size: contain;
        background-position: left center;
        margin-bottom: 8px;

        &--samsung {
            background-image: url("@/assets/logo/samsung.png");
        }
        &--samsung-digital {
            background-image: url("@/assets/logo/samsung-digital.png");
        }
        &--haier {
            background-image: url("@/assets/logo/haier.png");
        }
        &--lg {
            background-image: url("@/assets/logo/lg.png");
        }
        &--hotpoint {
            background-image: url("@/assets/logo/hotpoint.png");
        }
        &--indesit {
            background-image: url("@/assets/logo/indesit.png");
        }
        &--electrolux {
            background-image: url("@/assets/logo/electrolux.png");
        }
        &--bosch {
            background-image: url("@/assets/logo/bosch.png");
        }
        &--zugel {
            background-image: url("@/assets/logo/zugel.png");
        }
    }

    &__all {
        column-gap: 30px;
        column-count: 5;
    }

    &__all-item {
        list-style: none;
        margin-bottom: 16px;
        padding-left: 30px;
        padding-right: 16px;
        position: relative;
    }

    &__all-link {
        font-size: 17px;
        line-height: 20px;
        text-decoration: none;
        color: $text-color;
    }

    &__all-letter {
        position: absolute;
        left: 0;
        top: 0;
        font-weight: 700;
    }
}
</style>