<template>
  <div v-if="event" class="event-cover">
    <img 
    :src="event.imageSrc" 
    :alt="event.imageAlt"
    >
    <div class="info">
      <div class="info-top">{{ event.name }}</div>
      <div class="info-bottom">
        <div class="date"><img src="../assets/calendar.svg" alt="">{{ event.date }}</div>
        <div class="time"><img src="../assets/clock.svg" alt="">{{ event.time }}</div>
        <div class="price"><img src="../assets/dollar.svg" alt="">{{ `${event.price} ETB` }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['events', 'currentEvent', "event"],
};
</script>
