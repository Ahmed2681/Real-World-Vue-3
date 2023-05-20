<script setup>
import EventService from '../services/EventService'
import { onMounted, ref } from 'vue'

const eventDetail = ref(null)
const id = ref(123)

onMounted(() => {
  EventService.getEventDetail(id)
    .then((response) => {
      eventDetail.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <div class="event-card">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>
