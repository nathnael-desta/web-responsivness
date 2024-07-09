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
						<img
							src="../../public/assets/call.svg"
							alt="phone image"
              :class="{ hidden: chosenTab != 2 }"
						/>
						<div class="phoneNo" :class="{ hidden: chosenTab != 2 }">{{ phoneNo }}</div>
					</div>
				</div>

				<div class="smses">
					<div
						class="phone"
						v-for="phoneNo in event.contact.sms"
					>
						<img
							src="../../public/assets/sms.svg"
							alt="phone image"
              :class="{ hidden: chosenTab != 2 }"
						/>
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
