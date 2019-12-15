<template>
  <div>
    <div class="jobdetails">
      <h3 class="jobdetails__title">
        {{ jobDetails.title }}
      </h3>
      <p class="jobdetails__type">Type: {{ jobDetails.type }}</p>
      <p class="jobdetails__company">Company: {{ jobDetails.company }}</p>
      <p class="jobdetails__description">{{ jobDetails.description }}</p>
    </div>
  </div>
</template>

<script>
import mock from "../api/mock";

export default {
  name: "JobDetail",
  props: {
    activeJob: {
      type: Number,
      default: null
    }
  },
  data() {
    return {
      jobs: mock.jobs
    };
  },
  computed: {
    /**
     * Show only the selected item
     * @returns {Object}
     */
    jobDetails() {
      return this.jobs[this.activeJob];
    }
  }
};
</script>

<style scoped lang="scss">
.jobdetails {
  /*text-align: left;*/
}
</style>
