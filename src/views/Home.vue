<template>
  <div>
    <h1>Job Page</h1>
    <div class="columns">
      <section>
        <job-overview />
      </section>
      <section>
        <job-detail />
      </section>
    </div>
  </div>
</template>

<script>
import JobOverview from "../components/JobOverview";
import JobDetail from "../components/JobDetail";

export default {
  name: "home",
  components: {
    JobOverview: JobOverview,
    JobDetail: JobDetail
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
    width: calc(50% - 20px);
  }
}
</style>
