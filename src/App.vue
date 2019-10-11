<template lang="html">
  <div>
    <h1>DevJobs.com</h1>
    <jobs-list :jobs="jobs"></jobs-list>
  </div>
</template>

<script>
import JobsList from './components/JobsList.vue'
import JobsListItem from './components/JobsListItem.vue'
export default {
  name: 'app',
  data(){
    return{
      jobs: []
    }
  },
  mounted(){
    fetch('https://jobs.github.com/positions.json?')
    .then(res => res.json())
    .then(jobs => this.jobs = jobs)
  },
  components:{
    "jobs-list": JobsList,
    "jobs-list-item": JobsListItem
  }
}
</script>

<style lang="css" scoped>
</style>
