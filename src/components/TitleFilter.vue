<template lang="html">
  <div id="title-filter">
    <label for="input-box">Filter Jobs by Title: </label>
    <input id="input-box" type="text" v-model="searchQuery" v-on:keyup="filterByTitle" placeholder="Seach jobs by Title...">
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'Title-filter',
  data(){
    return{
      searchQuery: ""
    }
  },
  props: ['jobs'],
  methods: {
    filterByTitle(){
      eventBus.$emit('title-filtered', this.filteredJobs);
    }
  },
  computed: {
    filteredJobs() {
      if(this.searchQuery) {
        return this.jobs.filter((job) => {
          return job.title.toLowerCase().includes(this.searchQuery.toLowerCase());
        })
      }else{
        return this.jobs;
      }
    }
  }
}
</script>

<style lang="css" scoped>
#title-filter {
  display: inline-block;
  border-bottom: 1px dotted black;
  padding-bottom: 20px;
  width: auto;
  margin-left: 20px;
}
</style>
