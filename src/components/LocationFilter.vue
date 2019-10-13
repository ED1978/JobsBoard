<template lang="html">
  <div id="location-filter">
    <label for="location-select">Filter Jobs by Location: </label>
    <select id="location-select" v-model="selectedJob">
      <option v-for="job in this.filteredByTitle">{{job.location}}</option>
    </select>
  </div>

</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: "location-filter",
  data(){
    return{
      selectedJob: null,
      filteredByTitle: null
    }
  },
  mounted(){
    eventBus.$on('title-filtered', (filteredJobs) => {
      this.filteredByTitle = filteredJobs;
    })
  },
  methods: {
    handleSelect(){
      eventBus.$emit('location-filtered', this.filteredJobs)
    }
  },
  computed: {
    filteredJobs() {
      if(this.selectedJob) {
        return this.filteredByTitle.filter((job) => {
          return job.location.toLowerCase().includes(this.selectedJob.toLowerCase());
        })
      }else{
        return this.filteredByTitle;
      }
    }
  }
}
</script>

<style lang="css" scoped>
#location-filter {
  display: inline-block;
  border-bottom: 1px dotted black;
  padding-bottom: 20px;
  width: auto;
  margin-left: 20px;
  margin-top: 20px;
}
</style>
