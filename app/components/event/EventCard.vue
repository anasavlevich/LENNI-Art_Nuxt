<template>
    <article class="event-card">
        <NuxtLink :to="`/events/${data.slug}`" class="event-card__link">
            <picture class="event-card__picture">
                <source type="image/webp" :srcset="data.img_webp" />

                <img :src="data.img" :alt="data.alt" class="event-card__img" />
            </picture>

            <h4 class="event-card__title">{{ data.title }}</h4>

            <p class="event-card__description">{{ data.description }}</p>

            <time v-if="date" :datetime="data.date" class="event-card__time">
                {{ date }}
            </time>
        </NuxtLink>
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
        const date = new Date(props.data.date);
        return `${date.toLocaleDateString()} | начало ${date.toLocaleTimeString(
            "ru-RU",
            {
                hour: "2-digit",
                minute: "2-digit",
            },
        )}`;
    } catch {
        return null;
    }
});
</script>

<style lang="less">
.event-card {
    display: flex;
    width: 406px;
    max-width: 100%;
    min-width: 280px;

    &__link {
        display: flex;
        flex-direction: column;
        width: 100%;
        color: @black;
        text-decoration: none;

        &:hover {
            .event-card__title {
                color: @red;
                text-decoration-color: @red;
            }
        }
    }

    &__picture {
        display: block;
        position: relative;
        width: 100%;
        margin: 0 auto 25px;
        font-size: 0;
        text-decoration: none;
        overflow: hidden;

        &::after {
            content: "";
            display: block;
            width: 100%;
            padding-top: 107.16%;
        }
    }

    &__img {
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    &__title {
        margin: 0 0 15px;
        min-height: 65px;
        color: @black;
        font-size: 24px;
        font-weight: 600;
        line-height: 1.375;
        text-decoration: underline transparent;
        transition:
            color 0.2s,
            text-decoration-color 0.2s;

        @media @bw1660 {
            margin: 0 0 10px;
        }

        @media @bw1340 {
            min-height: 54px;
            font-size: 20px;
            line-height: 1.35;
        }

        @media @bw768 {
            min-height: 50px;
            font-size: 16px;
        }
    }

    &__description {
        margin: 0 0 auto;
        font-weight: 400;
        font-size: 16px;
        line-height: 1.375;

        @media @bw768 {
            font-size: 14px;
            line-height: 1.357;
        }
    }

    &__time {
        margin: 15px 0 auto;
        font-weight: 300;
        font-size: 14px;
        line-height: 1.357;
    }
}
</style>