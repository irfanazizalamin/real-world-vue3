<script setup>
import { ref, onMounted } from 'vue'
import EventCard from '@/components/EventCard.vue'
// import axios from 'axios'
import EventServices from '@/services/EventServices.js'

const events = ref(null)

onMounted(() => {
  EventServices.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>