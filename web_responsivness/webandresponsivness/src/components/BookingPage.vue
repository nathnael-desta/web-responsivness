<template>
  <div class="main">
		<div class="left">
			<event-cover
				:events="events"
				:current-event="currentEvent"
				:event="event"
			>
			</event-cover>

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

			<event-constraints :event="event"></event-constraints>
		</div>

		<div class="right">
			<event-form 
				:event="event"
				:page-created="pageCreated"
				:ticket-data="ticketData"
				:increase="increase"
				:decrease="decrease"
				></event-form>
		</div>
	</div>
</template>

<script>
import EventCover from './EventCover.vue';
import EventTitle from './EventTitle.vue';
import EventDetails from './EventDetails.vue';
import EventConstraints from './EventConstraints.vue';
import EventForm from './EventForm.vue';

export default {
  components: {
			EventCover,
			EventTitle,
			EventDetails,
			EventConstraints,
			EventForm,
		},
  props: ['events', 'currentEvent', 'event', 'pageCreated', 'ticketData', 'increase', 'decrease'],
}
</script>