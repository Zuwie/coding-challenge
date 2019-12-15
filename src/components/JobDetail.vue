<template>
  <div>
    <div class="jobdetails" v-if="job !== null">
      <h3 class="jobdetails__title">
        {{ job.title }}
      </h3>
      <p class="jobdetails__id">Job-ID: {{ job.id }}</p>
      <p class="jobdetails__userid">User-ID: {{ job.userId }}</p>
      <p class="jobdetails__description">{{ job.body }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "JobDetail",

  props: {
    activeJob: {
      type: Number,
      default: 1
    }
  },

  data() {
    return {
      job: null
    };
  },

  /**
   * Show data of selected item
   */
  mounted() {
    this.getJob(this.activeJob);
  },

  /**
   * Fetches data from Placeholder API https://jsonplaceholder.typicode.com/
   */
  methods: {
    getJob(id) {
      axios
        .get(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then(response => (this.job = response.data))
        .catch(error => {
          console.log(error);
        });
    }
  },

  /**
   * Listen to changes and react to them
   */
  watch: {
    activeJob() {
      this.getJob(this.activeJob);
    }
  }
};
</script>

<style scoped lang="scss">
.jobdetails {
  /*text-align: left;*/
}
</style>
