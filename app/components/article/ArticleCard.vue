<template>
    <article class="article-card">
        <a href="#" class="article-card__link">
            <picture class="article-card__pic">
                <source media="(max-width: 450px)" type="imgage/webp" :srcset="data.img_webp" />
                <source media="(max-width: 450px)" :srcset="data.img" />
                <source media="(max-width: 1169px)" type="imgage/webp" :srcset="data.img_tablet_webp" />
                <source media="(max-width: 1169px)" :srcset="data.img_tablet" />
                <source type="imgage/webp" :srcset="data.img_webp" />
                <img :src="data.img" :alt="data.alt" class="article-card__img" />
            </picture>
        </a>
        <div class="article-card__info">
            <time :datetime="data.date" class="article-card__time">{{ date }}</time>
            <a href="#" class="article-card__title-link">
                <span class="article-card__title">{{ data.title }}</span>
                <SvgIcon class=" article-card__arrow arrow__icon" name="arrow" width="92" height="62" />
            </a>
            <p class="article-card__description">{{data.description}}</p>
        </div>
    </article>
</template>

<script setup>
const props = defineProps({
    data: {
        type: Object,
        default: () => ({}),
    },
});
const date = computed(() => {
    try {
        return new Date(props.data.date).toLocaleDateString();
    } catch {
        return null;
    }
});
</script>

<style lang="less">
.article-card {
    box-sizing: border-box;
    position: relative;
    display: flex;
    flex-direction: row;
    width: 100%;

    &:hover {
        .article-card__pic {
            box-shadow: 0 0 30px rgba(31, 31, 30, 0.55);
        }
    }

    @media @bw1020 {
        flex-direction: column;
    }


    &__link {
        flex-shrink: 0;
        align-self: flex-start;
        display: block;
        width: 467px;
        margin-right: 60px;
        font-size: 0;
        text-decoration: none;

        &:hover {
            &~.article-card__info {
                .article-card__title-link {
                    color: @red;
                    text-decoration-color: @red;
                }
            }
        }

        @media @bw1020 {
            width: 100%;
        }
    }

    &__pic {
        display: block;
        position: relative;
        width: 100%;
        transition: box-shadow 0.2s;
        overflow: hidden;

        &::after {
            content: "";
            display: block;
            width: 100%;
            padding-top: 62.3126%;
        }
    }

    &__img {
        display: block;
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    &__info {
        box-sizing: border-box;
        position: relative;
        display: flex;
        flex-direction: column;
        width: 100%;
        padding-top: 30px;
        padding-bottom: 30px;
        padding: 30px 0;
        padding-right: 150px;
    }

    &__time {
        margin: 0 0 40px;
        font-weight: 300;
        font-size: 16px;
        line-height: 22px;
    }

    &__title-link,
    &__description {
        max-width: 470px;
    }

    &__title-link {
        margin: auto 0 40px;
        color: @black;
        text-decoration-color: transparent;
        transition: color 0.2s, text-decoration-color 0.2s;

        &:hover {
            color: @red;
            text-decoration-color: @red;
        }

        @media @bw500 {
            min-width: 280px;
            margin-top: -20px;
        }
    }

    &__title {
        margin: 0;
        color: inherit;
        font-weight: 700;
        font-size: 24px;
        line-height: 1.375;

        @media @bw960 {
            font-size: 20px;
        }

        @media @bw500 {
            font-size: 16px;
        }
    }

    &__description {
        margin: 0;
        font-size: 16px;
        line-height: 1.375;

        @media @bw500 {
            font-size: 14px;
            min-width: 260px;
            margin-top: -20px;
        }
         @media @bw370 {
            min-width: 240px;
         }
    }

    &__arrow {
        position: absolute;
        bottom: 30px;
        right: 0;
        background-color: transparent;
        border: none;
        color: inherit;
        transition: none;

        @media @bw500 {
            bottom: -40px;

            .arrow__icon {
                width: 67px;
            }
        }
    }

    &+.article-card {
        margin-top: 120px;

        &::before {
            content: "";
            display: block;
            position: absolute;
            margin: 0 auto 60px;
            bottom: 100%;
            left: 0;
            right: 0;
            width: 100%;
            max-width: 1254px;
            height: 1px;
            background-color: @black;
            pointer-events: none;
        }
    }
}
</style>