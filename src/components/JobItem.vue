<template>
  <li class="jobitem">
    <h3 class="jobitem__title">
      {{ job.title }}
    </h3>
    <p class="jobitem__user">UserID: {{ job.userId }}</p>
    <p class="jobitem__description">
      {{ job.body | truncate(50) }}
    </p>
    <button class="button" @click="setActiveJob(job.id)">
      More information about this job
    </button>
  </li>
</template>

<script>
export default {
  name: "JobItem",
  props: {
    job: {
      type: Object,
      default() {
        return {
          id: {
            type: Number,
            default: null
          },
          userId: {
            type: Number,
            default: null
          },
          title: {
            type: String,
            default: "Job Title"
          },
          body: {
            type: String,
            default: "Job Description"
          }
        };
      }
    }
  },
  methods: {
    /**
     * emmit selected id to parent so sibling component can display it
     * @param {number} id - The id value
     */
    setActiveJob(id) {
      this.$emit("setActiveJob", id);
    }
  }
};
</script>

<style scoped lang="scss">
.jobitem {
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: rgba(0, 0, 0, 0.15) 0 8px 16px 0;
  border-radius: 5px;
  transition: transform 0.2s ease;
  text-align: center;

  &.active-item {
    background: #aeffdf;
  }

  &__description {
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

.button {
  cursor: pointer;
  background: transparent;
  box-shadow: none;
  outline: none;
  padding: 11px 20px 12px;
  border: 1px solid #000000;
  text-transform: uppercase;
  font-weight: 700;
  font-size: 12px;
  line-height: 1.3;
  transition: 0.2s ease;

  &:hover {
    color: #fff;
    background: #000;
  }
}
</style>
