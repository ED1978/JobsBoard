<template lang="html">
  <div id="jobs-list-item" v-on:click="jobSelected">
    <h3>{{job.type}} <span>{{job.title}}</span></h3>
    <img v-bind:src="job.company_logo" alt="Companylogo">
    <h4>{{job.company}}</h4>
    <p>{{job.location}}</p>
    <job-detail v-if="selectedJob == this.job" :job="selectedJob"></Job-detail>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
import JobDetail from './JobDetail.vue'
export default {
  name: 'jobs-list-item',
  data(){
    return{
      selectedJob: null
    }
  },
  props: ['job'],
  mounted(){
    eventBus.$on('job-selected', (job) => {
      this.selectedJob = job;
    })
  },
  methods: {
    jobSelected(){
      eventBus.$emit('job-selected', this.job);
    }
  },
  components:{
    "job-detail": JobDetail
  }
}
</script>

<style lang="css" scoped>
#jobs-list-item {
  border: black 1px solid;
  height: auto;
  width: auto;
  margin: 20px;
}

img {
  width: 100px;
}
</style>
