<template>
	<div
    v-if="event"
		class="event-title"
	>
		<div class="title">{{ event.name }}</div>
		<div class="event-details-bottom">
			<div class="organizer">{{ event.organizer }}</div>
			<div 
      class="days-left yellow"
      >{{ daysText }}</div>
		</div>
	</div>
</template>

<script>
	export default {
		props: ['events', 'currentEvent', 'event'],
		computed: {
      activeClasses() {
        return {
          green: this.daysLeft > 3,
          yellow: this.daysLeft > 1 && this.daysLeft < 4,
          red: this.daysLeft === 0 || this.daysLeft === 1, 
          grey: this.daysLeft < 0
        }
      },
      daysLeft() {
        return this.daysUntil(this.events[this.currentEvent].date);
      },
			daysText() {

				if (this.daysLeft > 3) {
					return `${this.daysLeft} days left`;
				}
				if (this.daysLeft > 1) {
					return `${this.daysLeft} days left`;
				}
				if (this.daysLeft === 1) {
					return `${this.daysLeft} day left`;
				}
				if (this.daysLeft === 0) {
					return 'today';
				}

				return 'passed';
			},
		},
		methods: {
			daysUntil(targetDate) {
				const currentDate = new Date();

				const target = new Date(targetDate);

				let [day, month, year] = targetDate.split(' ');

				const months = {
					Jan: '01',
					Feb: '02',
					Mar: '03',
					Apr: '04',
					May: '05',
					Jun: '06',
					Jul: '07',
					Aug: '08',
					Sep: '09',
					Oct: '10',
					Nov: '11',
					Dec: '12',
				};

				month = months[month];

				const diffTime = target - currentDate;

				// from milliseconds to days

				const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

				return diffDays;
			},
		},
	};
</script>
