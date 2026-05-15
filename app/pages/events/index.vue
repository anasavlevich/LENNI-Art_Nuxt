<template>
  <div class="events">
    <AppListing :moreBtn="true" :url="'http://localhost:3000/json/events.json'" v-slot="{list}" title="Мероприятия"
      class="events__listing">
      <EventCard v-for="(card, index) in list" :key="index" :data="card" class="app-listing__card" />
    </AppListing>
    <EventsTable class="events__table" />
    <AppOffers />
    <EventsInfo />
  </div>
</template>

<script setup>
</script>

<style lang="less">
.events {
  padding: 140px 0 100px;

  &__listings {
    margin-bottom: 120px;
  }

  &__table {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 1334px;
    margin: 100px auto 0;
  }
}
</style>