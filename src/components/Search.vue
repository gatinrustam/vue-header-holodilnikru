<template>
    <div class="search">
        <div class="search__form">
            <input type="search" class="search__input" placeholder="Поиск по каталогу">
            <button type="submit" class="search__button">
                <img src="@/assets/search.svg" alt="search" />
            </button>
        </div>
    </div>
</template>

<style lang="scss">
.search {
    width: 100%;
    max-width: 630px;
    margin: 0 30px;

    &__form {
        position: relative;
        border-radius: 6px;
        border: 1px solid $primary-blue;
        display: flex;
        overflow: hidden;
        height: 45px;
    }

    &__input {
        width: 100%;
        font-size: 18px;
        line-height: 24px;
        padding: 10px 20px;
        border: none;

        &:hover,
        &:active,
        &:focus {
            outline: none;
        }
    }

    &__button {
        background-color: $primary-blue;
        color: #ffffff;
        border: none;
        outline: none;
        padding: 11px 28px 10px;
        cursor: pointer;
        transition: $transition;

        &:hover {
        background-color: $primary-blue-hover;
        }
    }

}
</style>