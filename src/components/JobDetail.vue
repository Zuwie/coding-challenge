<template>
  <div>
    <h2>Detail</h2>

    <div class="jobdetails">
      <h3 class="jobitem__title">
        {{ jobDetails.title }}
      </h3>
      <p class="jobitem__type">Type: {{ jobDetails.type }}</p>
      <p class="jobitem__company">Company: {{ jobDetails.company }}</p>
      <p class="jobitem__description">{{ jobDetails.description }}</p>
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
    jobDetails() {
      return this.jobs[this.activeJob];
    }
  }
};
</script>

<style scoped></style>
