<template>
	<div 
		class="tickets" 
		v-if="event"
		>
		<div class="label ticket-label" :class="[classes.label]">Tickets to Buy</div>
		<div class="tickets-container input" :class="[classes.buttons]">
			<div
				class="minus ticket-control"
				@click="decrease"
			></div>
			<div class="tickets-count">{{ ticketData.count }}</div>
			<div
				class="plus ticket-control"
				@click="increase"
			></div>
		</div>
		<div class="total-price">
			You'll be paying
			<span class="amount">{{ `&nbsp;${totalPrice}.00` }}</span> ETB
		</div>
	</div>
</template>

<script>

	export default {
	  props: ['event', 'ticketData', 'classes', 'count','increase','decrease'],
	  computed: {
				totalPrice() {
					return this.ticketData.count * this.event.price;
				},
	    },
	}
</script>

<style>

</style>