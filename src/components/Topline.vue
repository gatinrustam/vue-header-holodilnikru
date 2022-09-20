<template>
    <div class="topline">
        <div class="topline__inner">
            <div class="topline__region">Москва и область</div>

            <nav class="topline__menu">
                <ul class="topline__list">
                    <li 
                        v-for="item in toplineMenu" 
                        class="topline__item"
                        :class="{'topline__item--parent': item.hasChild}"
                    >
                        <a class="topline__link" :href="item.url">
                            {{item.title}}
                        </a>
                    </li>
                </ul>
            </nav>

            <div class="topline__contact">
                <div class="topline__callback">Заказать звонок</div>
                <div class="topline__phone">+7 (495) 232-06-00</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Topline',
    data() {
        return {
            toplineMenu: [
                {title: 'Магазины', url: '#', hasChild: false, },
                {title: 'Покупателям', url: '#', hasChild: true, },
                {title: 'Услуги', url: '#', hasChild: true, },
                {title: 'Бизнесу', url: '#', hasChild: true, },
            ]
        }
    }
}
</script>

<style lang="scss">
.topline {
    background-color: #f3f3f3;
    color: #464b51;
    padding: 8px 0;
    font-size: 17px;
    line-height: 32px;

    &__link {
        color: #464b51;
        text-decoration: none;
        padding: 0 0 0 16px;
    }

    &__inner {
        @include container;
        display: flex;
        align-items: center;
    }

    &__region {
        flex: 1 0 auto;
        padding-left: 32px;
        background-image: url('@/assets/geo.svg');
        background-position: left center;
        background-repeat: no-repeat;
    }

    &__list,
    &__item {
        list-style: none;
    }

    &__list {
        display: flex;
    }

    &__item {
        margin-right: 32px;
        border-radius: 6px;

        &:last-child {
            margin-right: 0;
        }

        &:hover {
            background-color: #e3e7ea;
        }

        &--parent {
            padding-right: 32px;
            background-image: url('@/assets/arrow-down.svg');
            background-position: right 12px center;
            background-repeat: no-repeat;
        }
    }

    &__contact {
        display: flex;
        flex: 1 0 auto;
        justify-content: flex-end;
    }

    &__callback {
        margin-right: 40px;
        padding-left: 32px;
        background-image: url('@/assets/phone.svg');
        background-position: left center;
        background-repeat: no-repeat;
    }

    &__phone {
        font-weight: 700;
    }
}
</style>