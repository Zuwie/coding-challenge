<template>
  <div>
    <h3>
      {{ job.title }}
    </h3>
  </div>
</template>

<script>
export default {
  name: "JobItem",
  props: {
    job: {
      type: Object,
      default() {
        return {
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
  }
};
</script>

<style scoped></style>
