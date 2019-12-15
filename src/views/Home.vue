<template>
  <div>
    <h1 class="page-title">Job Page</h1>

    <form class="filter-form" v-on:submit.prevent>
      <div class="filter-form__group">
        <label for="filterId" class="filter-form__label"
          >Search for User-ID:</label
        >
        <input
          type="text"
          id="filterId"
          class="filter-form__input"
          v-model="filterTerm"
        />
      </div>
    </form>

    <div class="columns ruler-between">
      <section class="section-overview">
        <h2 class="section-title">Job Overview</h2>
        <p v-if="loading">Loading...</p>
        <ul class="job-list" v-else>
          <job-item
            v-for="job in filteredResults"
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
      loading: true,
      filterTerm: ""
    };
  },

  mounted() {
    /**
     * Fill the app with data
     */
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
  },

  computed: {
    /**
     * Filter over the data
     * @returns {Object} - only those which match the filter
     */
    filteredResults() {
      const search = this.filterTerm.toLowerCase().trim();

      if (!search) return this.jobs;

      return this.jobs.filter(
        obj =>
          obj.userId
            .toString()
            .toLowerCase()
            .indexOf(search) > -1
      );
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

.filter-form {
  display: flex;
  justify-content: center;
  padding: 20px;
  margin-bottom: 40px;

  &__group {
    min-width: 280px;
  }
  &__label {
    font-weight: 700;
    margin-bottom: 0.5em;
  }
  &__input {
    display: block;
    width: 100%;
    height: 2em;
    border: 1px solid #eee;
    border-radius: 4px;
  }
}
</style>
