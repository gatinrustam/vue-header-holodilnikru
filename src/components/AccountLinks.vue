<template>
<div class="account">
    <a href="#" class="account__link">
        <img :src="Enter" alt="" />
        <span class="account__text">Войти</span>
    </a>
    <a href="#" class="account__link">
        <img :src="Favorite" alt="" />
        <span class="account__text">Избранное</span>
    </a>
    <a href="#" class="account__link">
        <img :src="Cart" alt="" />
        <span class="account__text">Корзина</span>
    </a>
</div>
</template>

<script>
import Enter from '@/assets/enter.svg';
import Favorite from '@/assets/fav.svg';
import Cart from '@/assets/cart.svg';

export default {
  name: 'AccountLinks',
  setup() {
    return {
        Enter,
        Favorite,
        Cart
    };
  }
}
</script>

<style lang="scss">
.account {
    display: flex;
    justify-content: space-between;
    flex: 1 0 auto;

    &__link {
        font-size: 17px;
        line-height: 20px;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        flex: 1;
        align-items: center;
        justify-content: center;
        text-decoration: none;
        color: $primary-blue;
        margin-right: 16px;

        &:last-child {
            margin-right: 0;
        }
    }

    &__text {
        text-align: center;

        @media screen and (max-width: $max-mobile) {
            display: none;
        }
    }
}
</style>