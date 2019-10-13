<template lang="html">
  <div>
    <header>
      <h1>DevJobs.com</h1>
      <search-filter id="search-filter"></search-filter>
    </header>
    <body>
      <jobs-list :jobs="jobs"></jobs-list>
    </body>
  </div>
</template>

<script>
import SearchFilter from './components/SearchFilter.vue'
import JobsList from './components/JobsList.vue'
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
    "search-filter": SearchFilter
  }
}
</script>

<style lang="css" scoped>
header{
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: white;
  width: 100%;
  opacity: 1;
  z-index: 10;
  padding-top: 0;
  border-bottom: 1px grey solid;
}

header h1{
  display: inline-block;
  margin-left: 20px;
}

#search-filter {
  display: inline-block;
  margin-right: auto;
  margin-left: 500px;
}

body {
  position: relative;
  margin-left: 0;
  padding-left: 0;
  top:60px;
  /* background-color: #867982; */
  width: 100%
}
</style>
