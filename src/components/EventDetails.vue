<template>
	<div class="event-details" v-if="event">
		<div class="tabs">
			<div class="about" @click="chosenTab = 0" :class="{chosen: chosenTab === 0}">About Event</div>
			<div class="location" @click="chosenTab = 1" :class="{chosen: chosenTab === 1}">Event Location</div>
			<div class="contact" @click="chosenTab = 2" :class="{chosen: chosenTab === 2}">Contact</div>
		</div>
		<div
			class="details"
			v-if="event"
		>
			<div
				class="about"
				:class="{ hidden: chosenTab != 0 }"
			>
				Lorem ipsum dolor sit amet consectetur. Sit egestas varius venenatis
				varius nisl lacus. Amet volutpat urna vitae id gravida amet est sed. A
				duis scelerisque aliquam posuere amet in tellus. Est senectus est nulla
				molestie.
			</div>

			<img
				:src="event.location"
				alt=""
				class="location"
				:class="{ hidden: chosenTab != 1 }"
			/>

			<div
				class="contact"
			>
				<div class="calls">
					<div
						class="phone"
						v-for="phoneNo in event.contact.call"
					>
          <svg :class="{ hidden: chosenTab != 2 }" width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M18.3083 15.2751C18.3083 15.5751 18.2416 15.8834 18.1 16.1834C17.9583 16.4834 17.775 16.7667 17.5333 17.0334C17.125 17.4834 16.675 17.8084 16.1666 18.0167C15.6666 18.2251 15.125 18.3334 14.5416 18.3334C13.6916 18.3334 12.7833 18.1334 11.825 17.7251C10.8666 17.3167 9.90829 16.7667 8.95829 16.0751C7.99996 15.3751 7.09163 14.6001 6.22496 13.7417C5.36663 12.8751 4.59163 11.9667 3.89996 11.0167C3.21663 10.0667 2.66663 9.11675 2.26663 8.17508C1.86663 7.22508 1.66663 6.31675 1.66663 5.45008C1.66663 4.88341 1.76663 4.34175 1.96663 3.84175C2.16663 3.33341 2.48329 2.86675 2.92496 2.45008C3.45829 1.92508 4.04163 1.66675 4.65829 1.66675C4.89163 1.66675 5.12496 1.71675 5.33329 1.81675C5.54996 1.91675 5.74163 2.06675 5.89163 2.28341L7.82496 5.00841C7.97496 5.21675 8.08329 5.40841 8.15829 5.59175C8.23329 5.76675 8.27496 5.94175 8.27496 6.10008C8.27496 6.30008 8.21663 6.50008 8.09996 6.69175C7.99163 6.88341 7.83329 7.08341 7.63329 7.28341L6.99996 7.94175C6.90829 8.03341 6.86663 8.14175 6.86663 8.27508C6.86663 8.34175 6.87496 8.40008 6.89163 8.46675C6.91663 8.53341 6.94163 8.58341 6.95829 8.63341C7.10829 8.90841 7.36663 9.26675 7.73329 9.70008C8.10829 10.1334 8.50829 10.5751 8.94163 11.0167C9.39163 11.4584 9.82496 11.8667 10.2666 12.2417C10.7 12.6084 11.0583 12.8584 11.3416 13.0084C11.3833 13.0251 11.4333 13.0501 11.4916 13.0751C11.5583 13.1001 11.625 13.1084 11.7 13.1084C11.8416 13.1084 11.95 13.0584 12.0416 12.9667L12.675 12.3417C12.8833 12.1334 13.0833 11.9751 13.275 11.8751C13.4666 11.7584 13.6583 11.7001 13.8666 11.7001C14.025 11.7001 14.1916 11.7334 14.375 11.8084C14.5583 11.8834 14.75 11.9917 14.9583 12.1334L17.7166 14.0917C17.9333 14.2417 18.0833 14.4167 18.175 14.6251C18.2583 14.8334 18.3083 15.0417 18.3083 15.2751Z" stroke="#171625" stroke-width="1.5" stroke-miterlimit="10"/>
</svg>

						<div class="phoneNo" :class="{ hidden: chosenTab != 2 }">{{ phoneNo }}</div>
					</div>
				</div>

				<div class="smses">
					<div
						class="phone"
						v-for="phoneNo in event.contact.sms"
					>
          <svg :class="{ hidden: chosenTab != 2 }" width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M14.1666 17.0834H5.83329C3.33329 17.0834 1.66663 15.8334 1.66663 12.9167V7.08341C1.66663 4.16675 3.33329 2.91675 5.83329 2.91675H14.1666C16.6666 2.91675 18.3333 4.16675 18.3333 7.08341V12.9167C18.3333 15.8334 16.6666 17.0834 14.1666 17.0834Z" stroke="#171625" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M14.1667 7.5L11.5584 9.58333C10.7 10.2667 9.2917 10.2667 8.43337 9.58333L5.83337 7.5" stroke="#171625" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
</svg>

						<div class="phoneNo" :class="{ hidden: chosenTab != 2 }">{{ phoneNo }}</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		props: ['events', 'currentEvent', 'event'],
		data() {
			return {
				chosenTab: 0,
			};
		},
    methods: {
      chooseTab(index) {

      }
    }
	};
</script>
