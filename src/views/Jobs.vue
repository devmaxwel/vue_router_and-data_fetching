<template>
  <h1>Jobs</h1>
  <div v-if="jobs">
    <div v-for="job in jobs" :key="job.id" class="job">
      <router-link :to="{ name: 'jobdetails', params: { id: job.id } }">
        <h2>{{ job.title }}</h2>
      </router-link>
    </div>
  </div>
  <div v-else>Jobs Loading....</div>
</template>

<script>
export default {
  data() {
    return {
      jobs: [],
    };
  },
  //   Mounted is like useEffect i react javascript
  mounted() {
    fetch("http://localhost:3000/jobs")
      .then((res) => {
        return res.json();
      })
      .then((data) => {
        return (this.jobs = data);
      })
      .catch((err) => {
        return console.log(err.message);
      });
  },
};
</script>


<style>
.job {
  background: #f4f4f4;
  padding: 15px;
  margin: 30px auto;
  max-width: 300px;
  border-radius: 20px;
  color: #444;
}
.job a {
  text-decoration: none;
}
</style>