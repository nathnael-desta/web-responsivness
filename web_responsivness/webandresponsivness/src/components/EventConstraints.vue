<template>
	<div class="event-constraints">
		<div class="date">
			<img
				src="../../public/assets/calendarO.svg"
				alt="calendar img"
			/>
			<div class="date">{{ event.date }}</div>
		</div>

    <div class="time">
      <img
				src="../../public/assets/clockO.svg"
				alt="clock img"
			/>
			<div class="date">{{ event.time }}</div>
    </div>

    <div class="price">
      <img
				src="../../public/assets/dollar-circleO.svg"
				alt="dollar img"
			/>
			<div class="date">{{ `${event.price} ETB/ticket` }}</div>
    </div>
	</div>
</template>

<script>
	export default {
		props: ['event'],
	};
</script>
