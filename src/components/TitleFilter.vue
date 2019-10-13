<template lang="html">
  <div id="title-select">
    <select v-on:change="handleSelect" v-model="selectedJob">
      <option disabled value="Filter by Job Title..."></option>
      <option v-for="job in jobs" :value="job">{{job.title}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'title-filter',
  props: ['jobs'],
  data(){
    return{
      selectedJob: null
    }
  },
  methods: {
    handleSelect(){
      eventBus.$emit('job-selected', this.selectedJob)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
