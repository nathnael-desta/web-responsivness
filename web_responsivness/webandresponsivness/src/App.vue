<template>
	<booking-page
		:events="events"
		:current-event="currentEvent"
		:event="event"
		:page-created="pageCreated"
		v-if="pageNo === 0"
		:ticket-data="ticketData"
    :increase="increase"
    :decrease="decrease"
    
	></booking-page>

	<payment-page
		:event="event"
		v-if="pageNo === 1"
		:ticket-data="ticketData"
		:change-page-no="changePageNo"
    :increase="increase"
    :decrease="decrease"
	></payment-page>

	<booking-success v-if="pageNo === 2"></booking-success>
</template>
<script>
	import BookingPage from './components/BookingPage.vue';
	import PaymentPage from './components/PaymentPage.vue';
	import BookingSuccess from './components/BookingSuccess.vue';

	export default {
		components: {
			BookingPage,
			PaymentPage,
			BookingSuccess,
		},
		computed: {
			event() {
				return this.events[this.currentEvent];
			},
		},
		data() {
			return {
				events: [],
				currentEvent: 0,
				pageNo: 0,
				buyers: [],
				ticketData: {
					name: '',
					phoneNo: '',
					count: 1,
					event: '',
					decrease() {
						if (this.count > 1) {
							this.count -= 1;
						}
						console.log('asdafasd', this.count);
					},
					increase() {
						this.count += 1;
						console.log('asfdasdf', this.count);
					},
				},
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
			pageCreated(dataObj) {
				this.buyers.push(dataObj);
				this.pageNo = 1;
				this.ticketData = {
					name: dataObj.name,
					phoneNo: dataObj.phoneNo,
					count: dataObj.count,
					event: dataObj.event,
				};

				console.log(dataObj, this.ticketData);
			},
			changePageNo(no) {
				this.pageNo = no;
			},
      increase() {
        this.ticketData.count +=1;
      },
      decrease() {
        if (this.ticketData.count > 0) {
          this.ticketData.count -= 1;
        }
      }
		},
	};
</script>
