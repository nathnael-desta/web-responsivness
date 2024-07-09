<template>
	<event-cover
		:events="events"
		:current-event="currentEvent"
    :event="event"
	>	</event-cover>

  <event-title
  		:events="events"
		  :current-event="currentEvent"
      :event="event"
  ></event-title>

  <event-details
      :events="events"
		  :current-event="currentEvent"
      :event="event"
  ></event-details>

  <event-constraints
    :event="event"
  ></event-constraints>

  <event-form
    :event="event"
  ></event-form>
</template>
<script>
	import EventCover from './components/EventCover.vue';
  import EventTitle from './components/EventTitle.vue';
  import EventDetails from './components/EventDetails.vue';
  import EventConstraints from './components/EventConstraints.vue';
  import EventForm from './components/EventForm.vue'
  
	export default {
		components: {
			EventCover,
      EventTitle,
      EventDetails,
      EventConstraints,
      EventForm
		},
    computed: {
      event() {
        return this.events[this.currentEvent];
      }
    },
		data() {
			return {
				events: [],
				currentEvent: 0,
			};
		},
		created() {
			this.getEvents();
		},
		methods: {
			async getEvents() {
				let res = await fetch('events.json');
				let data = await res.json();

				this.events = data;
			},
		},
	};
</script>
