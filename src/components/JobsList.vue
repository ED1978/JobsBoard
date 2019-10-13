<template lang="html">
  <div>
    <title-filter :jobs="jobs"></title-filter>
    <h2>Current Vacancies</h2>
    <ul>
      <jobs-list-item v-for="(job, index) in jobs" :job="job" :key="index"></jobs-list-item>
    </ul>
  </div>
</template>

<script>
import TitleFilter from './TitleFilter.vue'
import JobsListItem from './JobsListItem.vue'
export default {
  name: 'jobs-list',
  props: ['jobs'],
  components: {
    'jobs-list-item': JobsListItem,
    'title-filter': TitleFilter
  }
}
</script>

<style lang="css" scoped>
</style>
