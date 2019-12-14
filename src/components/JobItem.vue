<template>
  <li class="jobitem">
    <h3 class="jobitem__title">
      {{ job.title }}
    </h3>
    <p class="jobitem__type">Type: {{ job.type }}</p>
    <p class="jobitem__company">Company: {{ job.company }}</p>
    <p class="jobitem__description">
      {{ job.description | truncate(50) }}
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
          title: {
            type: String,
            default: "Job Title"
          },
          type: {
            type: String,
            default: "Job Type"
          },
          company: {
            type: String,
            default: "Job Company"
          },
          description: {
            type: String,
            default: "Job Description"
          }
        };
      }
    }
  },
  methods: {
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

  &__description {
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

.button {
  cursor: pointer;
  background: #ffffff;
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
