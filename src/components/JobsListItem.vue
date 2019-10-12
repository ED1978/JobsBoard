<template lang="html">
  <div id="jobs-list-item">
    <div class="box-text">
      <h2>{{job.type}} <span>{{job.title}}</span></h2>
      <img v-bind:src="job.company_logo" alt="Companylogo">
      <h4>Company: {{job.company}}</h4>
      <p>Location: {{job.location}}</p>
      <button v-on:click="jobSelected" type="button" name="button">Details</button>
      <job-detail v-if="this.job == selectedJob" :job="selectedJob"></job-detail>
    </div>
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
    }),

    eventBus.$on('close-details', () => {
      this.selectedJob = null;
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
  display: block;
  border: black 1px solid;
  height: auto;
  width: 50%;
  margin-left: auto;
  margin-right: auto;
  margin-top: 30px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 3px 6px #888888;
}

img {
  width: 100px;
}

.box-text {
  margin: 15px;
}

</style>
