<template>
	<div
		class="event-form"
		v-if="event"
	>
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
				placeholder="Abebe Bikila"
			/>
		</div>

		<div class="phone-number">
			<label
				for=""
				class="phone-number-label label"
				>Phone Number</label
			>
			<div class="input-container">
				<input
					type="number"
					class="phone-number-input input fullwidth"
					v-model="phoneNo"
					placeholder="00 00 00 00"
				/>
			</div>
		</div>

		<tickets-count
      :count="count"
      :event="event"
      :decrease="decrease"
      :increase="increase"
      :ticket-data="ticketData"
      v-if="event"
      :classes="{label:'', buttons: ''}"
    ></tickets-count>

		<button
			class="submit"
			:class="{ disable: filled }"
			@click.prevent="submitForm"
		>
			I'm ready to pay<span class="submit-amount"
				>&nbsp;{{ totalPrice }}.00&nbsp;</span
			>
			Birr
		</button>
	</div>
</template>

<script>
  import TicketsCount from "./TicketsCount.vue"

	export default {
    components: {TicketsCount},
    emits: ['page-created'],
		props: ['event', 'pageCreated', 'ticketData'],
		data() {
			return {
				name: '',
				phoneNo: '',
				count: 1,
			};
		},
		computed: {
			totalPrice() {
				return this.ticketData.count * this.event.price;
			},
			filled() {
				return !this.name || !this.phoneNo;
			},
		},
		methods: {
			submitForm() {
				if (!this.name || !this.phoneNo) {
					alert('Please fill the form.');
					return;
				}
        
				this.pageCreated({
					name: this.name,
          phoneNo: this.phoneNo,
          count: this.ticketData.count,
          event: this.event
				});

			},
      decrease() {
					if (this.count > 1) {
						this.count -= 1;
					}
				},
				increase() {
					this.count += 1;
				},
		},
	};
</script>
