<template lang="html">
  <div id="location-filter">
    <label for="location-select">Filter Jobs by Location: </label>
    <select id="location-select" v-on:change="handleSelect" v-model="selectedJob">
      <option v-for="job in this.filteredByTitle">{{job.location}}</option>
    </select>
  </div>

</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: "location-filter",props: ['jobs'],
  data(){
    return{
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
