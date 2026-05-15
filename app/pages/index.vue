<template>
  <div>
    <AppIntro class="home__intro" />
    <AppOffers class="home__offers" />
    <AppAbout class="home__about" />
    <EventsUpcoming class="home__upcoming" />
    <AppListing :moreLink="true" :grid="'column'" :url="'http://localhost:3000/json/blog.json'" v-slot="{ list }"
      title="Блог" class="home__listing">
      <ArticleCard v-for="card in list" :key="card.slug" :data="card" />
    </AppListing>
    <AppContacts class="home__contacts" />
  </div>
</template>

<script setup>
</script>

<style lang="less">
.home {
  &__listing {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 1414px;
    margin: 0 auto 100px;
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
  }
}
</style>