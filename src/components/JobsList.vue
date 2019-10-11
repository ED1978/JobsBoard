<template lang="html">
  <div>
    <h2>Current Vacancies</h2>
    <ul>
      <jobs-list-item v-for="(job, index) in jobs" :job="job" :key="index"></jobs-list-item>
    </ul>
  </div>
</template>

<script>
import JobsListItem from './JobsListItem.vue'
export default {
  name: 'jobs-list',
  props: ['jobs'],
  components: {
    'jobs-list-item': JobsListItem
  }
}
</script>

<style lang="css" scoped>
</style>
