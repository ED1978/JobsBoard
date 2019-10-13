<template lang="html">
  <div id="jobs-list">
    <ul>
      <jobs-list-item v-for="(job, index) in this.filteredJobs" :job="job" :key="index"></jobs-list-item>
    </ul>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
import JobsListItem from './JobsListItem.vue'
export default {
  name: 'jobs-list',
  data(){
    return{
      filteredJobs: null
    }
  },
  // props: ['jobs'],
  components: {
    'jobs-list-item': JobsListItem
  },
  mounted(){
    eventBus.$on('title-filtered', (filteredJobs) => {
      this.filteredJobs = filteredJobs;
    })
  }
}
</script>

<style lang="css" scoped>
#jobs-list {
  position: relative;
  top: 30px;
}
</style>
