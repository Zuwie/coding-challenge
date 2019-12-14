<template>
  <div>
    <h2>Job Overview</h2>
    <ul>
      <job-item v-for="job in jobs" :key="job.id" :job="job" />
    </ul>
  </div>
</template>

<script>
import mock from "../api/mock";
import JobItem from "./JobItem";

export default {
  name: "JobOverview",
  components: {
    JobItem: JobItem
  },
  data() {
    return {
      jobs: mock.jobs
    };
  }
};
</script>

<style scoped></style>
