<template>
  <div>
    <h1>Job Page</h1>
    <main class="content-container columns">
      <section>
        <h2>Job Overview</h2>
        <ul class="job-list">
          <job-item
            v-for="job in jobs"
            :key="job.id"
            :job="job"
            @setActiveJob="setActiveJob($event)"
          />
        </ul>
      </section>
      <section>
        <job-detail :activeJob="activeJob" v-if="activeJob !== null" />
      </section>
    </main>
  </div>
</template>

<script>
import mock from "../api/mock";
import JobItem from "../components/JobItem";
import JobDetail from "../components/JobDetail";

export default {
  name: "home",
  components: {
    JobItem: JobItem,
    JobDetail: JobDetail
  },
  data() {
    return {
      jobs: mock.jobs,
      activeJob: null
    };
  },
  methods: {
    setActiveJob(id) {
      this.activeJob = id;
    }
  }
};
</script>

<style scoped lang="scss">
.content-container {
  position: relative;
  &::after {
    @media screen and (min-width: 1024px) {
      content: "";
      position: absolute;
      left: 50%;
      top: 0;
      display: block;
      height: 100%;
      width: 1px;
      background: #eeeeee;
    }
  }
}

.columns {
  @media screen and (min-width: 1024px) {
    display: flex;
    justify-content: space-between;

    > * {
      width: calc(50% - 20px);
    }
  }
}

.job-list {
  padding: 0;
  margin: 0;
}
</style>
