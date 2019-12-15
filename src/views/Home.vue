<template>
  <div>
    <h1 class="page-title">Job Page</h1>
    <div class="columns ruler-between">
      <section class="section-overview">
        <h2 class="section-title">Job Overview</h2>
        <ul class="job-list">
          <job-item
            v-for="job in jobs"
            :key="job.id"
            :job="job"
            :class="job.id === activeJob ? 'active-item' : ''"
            @setActiveJob="setActiveJob($event)"
          />
        </ul>
      </section>
      <section class="section-details">
        <h2 class="section-title">Details:</h2>
        <job-detail :activeJob="activeJob" v-if="activeJob !== null" />
      </section>
    </div>
  </div>
</template>

<script>
import mock from "@/api/mock";
import JobItem from "@/components/JobItem";
import JobDetail from "@/components/JobDetail";

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
    /**
     * Gets triggered by emmited event
     * @param {Number} id - The id value
     */
    setActiveJob(id) {
      this.activeJob = id;
    }
  }
};
</script>

<style scoped lang="scss">
.columns {
  @media screen and (min-width: 1024px) {
    display: flex;
    justify-content: space-between;

    > * {
      width: calc(50% - 20px);
      padding: 20px;
    }
  }
}

.ruler-between {
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

.page-title {
  text-align: center;
  text-transform: uppercase;
  margin-bottom: 3em;
}

.section-title {
  text-align: center;
  text-transform: uppercase;
  margin-bottom: 2em;
}
</style>
