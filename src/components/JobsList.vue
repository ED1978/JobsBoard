<template lang="html">
  <div>
    <ul>
      <jobs-list-item v-for="(job, index) in filteredJobs" :job="job" :key="index"></jobs-list-item>
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
      searchQuery: "",
      filter: ['title', 'location', 'type']
    }
  },
  props: ['jobs'],
  components: {
    'jobs-list-item': JobsListItem
  },
  mounted(){
    eventBus.$on('search-query', (query) => {
      this.searchQuery = query;
    })
  },
  computed: {
    filteredJobs() {
      if(this.searchQuery) {
        return this.jobs.filter((job) => {
          return job.location.toLowerCase().includes(this.searchQuery.toLowerCase());
        })
      }else{
        return this.jobs;
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
