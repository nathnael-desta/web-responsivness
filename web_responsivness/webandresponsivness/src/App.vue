<template>
	<event-poster
		:events="events"
		:current-event="currentEvent"
	>
	</event-poster>
</template>
<script>
	import EventPoster from './components/EventPoster.vue';
	export default {
		components: {
			EventPoster,
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
				console.log('the events are ', this.events[0]);
			},
		},
	};
</script>
