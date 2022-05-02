<template>
  <h1>Job Details page</h1>
  <div v-if="job">
    <p>Job Title: {{ job.title }}</p>
    <p>The Job Id is {{ id }}</p>
    <p>Role: {{ job.details }}</p>
  </div>
  <div v-else>
     Job Loading......
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      job: null,
    };
  },
  mounted() {
    fetch(`http://localhost:3000/jobs/${this.id}`)
      .then((res) => {
        return res.json();
      })
      .then((data) => {
        return (this.job = data);
      })
      .catch((err) => {
        return console.log(err.message);
      });
  },
};
</script>

<style>
</style>