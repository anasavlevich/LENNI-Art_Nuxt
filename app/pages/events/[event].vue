<template>
  <article class="event">
    <header class="event__header">
      <h1 class="event__title title">{{ data.title }}</h1>
      <div class="event__about">
        <div class="event__info1">
          <time v-if="datetime" :datetime="data.date" class="event__time">
            {{ datetime.date }}
          </time>
          <div class="event__info-text">{{ data.location }}</div>
        </div>
        <picture class="event__picture">
          <source type="image/webp" :srcset="data.img_webp" />
          <img :src="data.img" :alt="data.alt" class="event__image" />
        </picture>
        <div class="event__info2">
          <span v-if="datetime" class="event__time" data-caption="начало">
            {{ datetime.time }}
          </span>
          <div class="event__info2-text">{{ data.address }}</div>
        </div>
      </div>
    </header>
    <div class="event__container">
      <div class="content event__content" v-html="data.content"></div>
    </div>
  </article>
</template>

<script setup>
const slug = computed(() => useRoute().params.event);
const URL = computed(
  () => `http://localhost:3000/json/events/${slug.value}.json`,
);

const { data } = await useFetch(URL);

const datetime = computed(() => {
  try {
    const date = new Date(data.value.date);
    return {
      date: date.toLocaleDateString(),
      time: date.toLocaleTimeString("ru-RU", {
        hour: "2-digit",
        minute: "2-digit",
      }),
    };
  } catch {
    return null;
  }
});
</script>

<style lang="less">
.event {
  &__title {
    text-align: center;
    font-family: @font2;
    font-weight: 500;
    font-size: 70px;

    @media @bw960 {
      font-size: 40px;
    }

    @media @bw600 {
      font-size: 30px;
    }

    @media @bw500 {
      font-size: 20px;
    }
  }

  &__about {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 58px;
    margin: 80px auto 80px;

    @media @bw1660 {
      gap: 50px;
    }

    @media @bw960 {
      gap: 40px;
      margin: 60px auto 75px;
    }

    @media @bw600 {
      margin: 40px auto 60px -10px;
      display: grid;
      grid-template-columns: 42% 42%;
      gap: 40px 20px;
      grid-template-areas:
        "pic pic"
        "details1 details2";
      justify-items: center;
    }

    @media @bw500 {
      margin: 40px auto 60px -20px;
    }

    @media @bw370 {
      margin-left: -15px;
    }
  }

  &__info1,
  &__info2 {
    display: inline-flex;
    flex-direction: column;
    max-width: 200px;
    font-family: @font3;
    font-size: 16px;
    font-weight: 700;
    text-transform: uppercase;
    text-wrap: nowrap;

    @media @bw960 {
      max-width: 160px;
      font-size: 12px;
    }
  }

  &__info1 {
    grid-area: details1;

    &::before,
    &::after {
      display: block;
      content: "";
      margin: 5px 0 5px;
      height: 1px;
      width: 100%;
      background: #ffffff;
      background: linear-gradient(90deg,
          rgba(255, 255, 255, 0) 39%,
          rgba(0, 0, 0, 1) 100%);

      @media @bw600 {
        width: 50%;
        align-self: flex-end;
      }
    }

    @media @bw600 {
      justify-self: right;
    }
  }

  &__info2 {
    grid-area: details2;

    &::before,
    &::after {
      display: block;
      content: "";
      margin: 5px 0 5px;
      height: 1px;
      width: 100%;
      background: #ffffff;
      background: linear-gradient(270deg,
          rgba(255, 255, 255, 0) 38%,
          rgba(0, 0, 0, 1) 100%);

      @media @bw600 {
        width: 50%;
      }
    }

    @media @bw600 {
      justify-self: left;
    }
  }

  &__time {
    font-size: 30px;
    font-weight: 300;

    @media @bw960 {
      font-size: 18px;
    }
  }

  &__info2-text {
    display: flex;
    flex-direction: row;
    align-items: baseline;
    justify-content: space-between;

    @media @bw960 {
      justify-content: flex-start;
      gap: 7px;
    }
  }

  &__picture {
    grid-area: pic;
    display: block;
    max-width: 506px;

    @media @bw1660 {
      max-width: 426px;
    }

    @media @bw960 {
      max-width: 35.5%;
    }

    @media @bw600 {
      max-width: 91%;
      width: 100%;
      margin-left: 40px;
    }

    @media @bw500 {
      margin-left: 30px;
    }

    @media @bw370 {
      margin-left: 20px;
    }
  }
}
</style>