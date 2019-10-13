<template lang="html">
  <div>
    <header>
      <h1>DevJobs.com</h1>
    </header>
    <body>
      <jobs-list :jobs="jobs"></jobs-list>
    </body>
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
header{
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  /* background-color:; */
  width: 100%;
  opacity: 1;
  z-index: 10;
  padding-top: 0;
}

header h1{
  margin-left: 20px;
}

body {
  position:relative;
  top:100px;
}
</style>
