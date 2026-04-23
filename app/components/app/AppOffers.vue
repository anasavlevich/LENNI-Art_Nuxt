<template>
    <section class="app-offers">
        <h4 class="app-offers__title">Я хочу:</h4>
        <div class="app-offers__btns">
            <button type="button" class="app-offers__btn btn btn--red" @click="openPopup()">
                Провести мероприятие
            </button>
            <button type="button" class="app-offers__btn btn">
                Стать арендатором
            </button>
        </div>
        <ModalWindow :name="'getOffer'" :title="' Заполните форму<br/>и мы подберем площадку'"></ModalWindow>
    </section>
</template>

<script setup>
const store = useStore();
const openPopup = () => {
    store.openModal("getOffer");
};
</script>

<style lang="less">
.app-offers {
    margin-bottom: 200px;

    &__title {
        text-align: center;
        text-wrap: nowrap;
        margin-left: 15px;
        margin-bottom: 46px;
        font-family: @font2;
        font-weight: 400;
        font-size: 22px;
        line-height: 30px;
        text-transform: uppercase;

        @media @bw1660 {
            font-size: 22px;
        }

        @media @bw960 {
            font-size: 16px;
        }

        @media @bw370 {
            margin-bottom: 25px;
            font-size: 13px;
        }
    }

    &__btns {
        box-sizing: border-box;
        display: flex;
        flex-direction: row;
        justify-content: center;
        gap: 106px;
        width: 100%;

        @media @bw768 {
            flex-direction: column-reverse;
            max-width: 280px;
            margin-left: auto;
            margin-right: auto;
            gap: 25px;
        }
    }

}
</style>