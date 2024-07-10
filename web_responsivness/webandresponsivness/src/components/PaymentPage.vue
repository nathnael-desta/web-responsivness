<template>
	<div class="payment-page">
		<div
			class="nav"
			v-if="event"
		>
			<div
				class="svg-container"
				@click="changePageNo(0)"
			>
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M15.0001 19.92L8.48009 13.4C7.71009 12.63 7.71009 11.37 8.48009 10.6L15.0001 4.07996"
						stroke="#292D32"
						stroke-width="1.5"
						stroke-miterlimit="10"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</div>
			<div
				class="title"
				id="nav-title"
			>
				{{ event.name }}
			</div>
		</div>

		<div class="ticket_container">
			<tickets-count
				:ticket-data="ticketData"
				:event="event"
				:classes="{ label: 'ticket-label', buttons: 'buttons' }"
			></tickets-count>
		</div>

		<div class="choosePayment">
			<div class="choose">Choose Payment Method</div>
			<div class="payment">
				<img
					src="../../public/assets/telebirr.svg"
					alt=""
          :class="{ chosenPayment: paymentNo == 1 }"
          @click="chooseDiv(1)"
				/>
				<img
					src="../../public/assets/cbebirr.svg"
					alt=""
          :class="{ chosenPayment: paymentNo == 2 }"
          @click="chooseDiv(2)"
				/>
				<img
					src="../../public/assets/Abbyssiniya.svg"
					alt=""
          :class="{ chosenPayment: paymentNo == 3 }"
          @click="chooseDiv(3)"
				/>
				<img
					src="../../public/assets/bank.svg"
					alt=""
          :class="{ chosenPayment: paymentNo == 4 }"
          @click="chooseDiv(4)"
				/>
				<img
					src="../../public/assets/CBE.svg"
					alt=""
          :class="{ chosenPayment: paymentNo == 5 }"
          @click="chooseDiv(5)"
				/>
			</div>
		</div>

		<div 
      class="payNow"
      :class="{disable: cantPay}"
    >Pay Now</div>
	</div>
</template>

<script>
	import TicketsCount from './TicketsCount.vue';
	export default {
		props: ['event', 'ticketData', 'changePageNo'],
    data() {
      return {
        paymentNo: NaN,
        cantPay: true
      }
    },
		components: { TicketsCount },
    methods: {
      chooseDiv(no) {
        this.paymentNo = no;
        this.cantPay = false;
      }
    }
	};
</script>
