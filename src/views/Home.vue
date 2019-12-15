<template>
  <div>
    <h1 class="page-title">Job Page</h1>

    <div class="columns ruler-between">
      <section class="section-overview">
        <h2 class="section-title">Job Overview</h2>
        <p v-if="loading">Loading...</p>
        <ul class="job-list" v-else>
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
import JobItem from "@/components/JobItem";
import JobDetail from "@/components/JobDetail";
import axios from "axios";

export default {
  name: "home",

  components: {
    JobItem: JobItem,
    JobDetail: JobDetail
  },

  data() {
    return {
      jobs: null,
      activeJob: null,
      loading: true
    };
  },

  mounted() {
    this.getJobs();
  },

  methods: {
    /**
     * Gets triggered by emmited event
     * @param {Number} id - The id value
     */
    setActiveJob(id) {
      this.activeJob = id;
    },

    /**
     * Fetches data from Placeholder API https://jsonplaceholder.typicode.com/
     */
    getJobs() {
      axios
        .get(`https://jsonplaceholder.typicode.com/posts`)
        .then(response => (this.jobs = response.data))
        .catch(error => {
          console.log(error);
        })
        .finally(() => (this.loading = false));
    }
  }
};
</script>

<style scoped lang="scss">
.columns {
  @media screen and (min-width: 1024px) {
    display: flex;
    justify-content: space-between;
  }

  > * {
    padding: 20px;
    @media screen and (min-width: 1024px) {
      width: calc(50% - 20px);
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
