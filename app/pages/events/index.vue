<template>
  <div class="events">
    <AppListing title="Мероприятия" class="events__listing">
      <EventCard
        v-for="(card, index) in list"
        :key="index"
        :data="card"
        class="app-listing__card"
      />
    </AppListing>
  </div>
</template>

<script setup>
  const list = ref([]);
  const URL = "http://localhost:3000/json/events.json";
  const { data } = await useAsyncData(`events`, () => {
    return $fetch(URL);
  });
  if (data?.value) list.value = data.value;
</script>

<style lang="less">
  .events {
  padding: 140px 0 100px;
  &__listings {
    margin-bottom: 120px;
  }
}
</style>