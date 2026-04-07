<template>
    <section class="app-listing">
        <h1 class="app-listing__title section-title">{{ title }}</h1>
        <div class="app-listing__list">
            <slot />
        </div>
        <button type="button" class="more-btn app-listing__more-btn">
            Показать всё
            <SvgIcon class="more-btn__arrow" name="arrow" width="92" height="62" />
        </button>
    </section>
</template>

<script setup>
const props = defineProps({
    title: {
        type: String,
        default: "",
    },
});
</script>

<style lang="less">
.app-listing {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 1414px;
    margin: 0 auto;
    padding-left: 40px;
    padding-right: 40px;

    @media @bw500 {
        margin-top: -40px;
    }

    @media @bw400 {
        margin-top: -60px;
    }

    @media @bw370 {
        margin-top: -70px;
    }

    &__title {
        @media @bw370 {
            min-width: 280px;
            margin-left: -12%;
        }
    }

    &__list {
        display: flex;
        flex-wrap: wrap;
        margin: 0 -29px;

        @media @bw1340 {
            margin: 0 -20px auto;
        }

        @media @bw1020 {
            justify-content: center;
            margin: 0 -15px auto;
        }

        @media @bw768 {
            margin: 0 -10px auto;
        }

        @media @bw650 {
            margin: 0 0 auto;
        }
    }

    &__card {
        width: calc(33.3333% - 58px);
        margin: 0 29px 120px;

        @media @bw1660 {
            width: calc(33.3333% - 40px);
            margin: 0 20px 90px;
        }

        @media @bw1340 {
            width: calc(33.3333% - 40px);
            max-width: 405px;
            margin: 0 17px 70px;
        }

        @media @bw1020 {
            width: calc(50% - 30px);
            max-width: 405px;
            margin: 0 15px 80px;
        }

        @media @bw768 {
            margin: 0 10px 80px;
            width: 100%;
            margin: 0 0 60px;
        }
    }

    &__more-btn {
        display: inline-flex;
        flex-direction: column;
        gap: 35px 0;
        align-self: center;
        align-items: center;
        background-color: transparent;
        border-color: transparent;
        font-family: @font1;
        font-weight: 600;
        font-size: 16px;
        line-height: 22px;
        text-decoration: none;
        transition: color 0.2s;

        &:hover {
            color: @red;
            cursor: pointer;
        }
    }
}
.more-btn__arrow {
    transform: rotate(90deg);
}
</style>