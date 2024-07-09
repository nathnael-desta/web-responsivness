<template>
  <div v-if="events" class="event-container">
    <img 
    :src="event.imageSrc" 
    :alt="event.imageAlt"
    >
    <div class="info">
      <div class="info-top">{{ event.name }}</div>
      <div class="info-bottom">
        <div class="date"><img src="../assets/calendar.svg" alt="">{{ event.date }}</div>
        <div class="time"><img src="../assets/clock.svg" alt="">{{ event.time }}</div>
        <div class="price"><img src="../assets/dollar.svg" alt="">{{ event.price }}</div>
      </div>
    </div>
  </div>

  <div v-if="events" class="event-details">
    <div class="title">{{ event.name }}</div>
    <div class="event-details-bottom">
      <div class="organizer">{{ event.organizer }}</div>
      <div class="days-left">{{ daysText }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props:['events', 'currentEvent'],
  computed: {
    event() {
      console.log("events", this.events)
      console.log("currentEvent", this.currentEvent)
      return this.events[this.currentEvent];
    },
    daysText() {
      const daysLeft = this.daysUntil(this.events[this.currentEvent].date)
      console.log(daysLeft);
      if (daysLeft > 3) {
        return `${daysLeft} days left`;
      }
      if (daysLeft > 1) {
        return `${daysLeft} days left`;
      }
      if (daysLeft === 1) {
        return `${daysLeft} day left`;
      }
      if (daysLeft === 0) {
        return 'today';
      }

      return 'passed';
    }
  },
  methods: {
    daysUntil(targetDate) {
      const currentDate = new Date();

      const target = new Date(targetDate);

      let [day, month, year] = targetDate.split(" ");


      const months = {
        Jan: "01",
        Feb: "02",
        Mar: "03",
        Apr: "04",
        May: "05",
        Jun: "06",
        Jul: "07",
        Aug: "08",
        Sep: "09",
        Oct: "10",
        Nov: "11",
        Dec: "12"
      }

      month = months[month];

      const diffTime = target - currentDate;
      
      // from milliseconds to days

      const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

      return diffDays;

    }
  }
};
</script>
