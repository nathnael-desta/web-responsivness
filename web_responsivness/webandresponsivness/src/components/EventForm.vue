<template>
	<div class="event-form">
		<div class="name">
			<label
				for=""
				class="name-label label"
			>
				Full Name
			</label>

			<input
				type="text"
				class="name-input input"
				v-model="name"
			/>
		</div>

		<div class="phone-number">
			<label
				for=""
				class="phone-number-label label"
				>Phone Number</label
			>
			<input
				type="text"
				class="phone-number-input input"
				v-model="phoneNo"
			/>
		</div>

		<div class="tickets">
      <div class="label ticket-label">Tickets to Buy</div>
			<div class="tickets-container input">
				<div class="minus ticket-control"></div>
				<div class="tickets-count">{{ count }}</div>
				<div class="plus ticket-control"></div>
			</div>
			<div class="total-price">
				You'll be paying
				<span class="amount">{{ `${totalPrice}.00` }}</span> ETB
			</div>
		</div>

		<div class="submit">
			I'm ready to pay <span class="amount">{{ totalPrice }}</span> Birr
		</div>
	</div>
</template>

<script>
	export default {
		props: ['event'],
		data() {
			return {
				name: '',
				phoneNo: '',
				count: 1,
			};
		},
		computed: {
			totalPrice() {
				return this.count * this.event.price;
			},
		},
	};
</script>
