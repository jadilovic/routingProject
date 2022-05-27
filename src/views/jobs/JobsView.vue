<template>
	<h1>Jobs</h1>
	<div v-if="jobs.length">
		<div v-for="job in jobs" :key="job.id" class="job">
			<router-link :to="{ name: 'job-details', params: { id: job.id } }">
				<h2>{{ job.title }}</h2>
			</router-link>
		</div>
	</div>
	<div v-else>
		<h2>Loading jobs...</h2>
	</div>
</template>

<script>
export default {
	data() {
		return {
			jobs: [],
		};
	},
	mounted() {
		fetch('http://localhost:3000/jobs')
			.then((res) => res.json())
			.then((data) => (this.jobs = data))
			.catch((err) => console.log(err.message));
	},
};
</script>

<style>
.job h2 {
	background: #ddd;
	padding: 20px;
	border-radius: 10px;
	margin: 10px auto;
	max-width: 600px;
	cursor: pointer;
	color: black;
}
.job h2:hover {
	background: lightslategray;
}
.job a {
	text-decoration: none;
}
</style>
