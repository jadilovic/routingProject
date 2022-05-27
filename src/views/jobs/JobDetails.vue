<template>
	<div v-if="job">
		<h1>Job Details</h1>
		<p>Job parameter : {{ id }}</p>
		<p>Title: {{ job.title }}</p>
		<p>Description: {{ job.description }}</p>
	</div>
	<div v-else>
		<p>Loading job data...</p>
	</div>
</template>

<script>
export default {
	props: ['id'],
	data() {
		return {
			job: null,
		};
	},
	mounted() {
		fetch('http://localhost:3000/jobs/' + this.id)
			.then((res) => res.json())
			.then((data) => (this.job = data))
			.catch((err) => console.log(err.message));
	},
	// data() {
	// 	return {
	// 		id: this.$route.params.id,
	// 	};
	// },
};
</script>

<style></style>
