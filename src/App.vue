<template lang="html">
  <div>
    <header>
      <h1>DevJobs.com</h1>
    </header>
    <filter-bar id="filter-bar"></filter-bar>
    <body>
      <jobs-list :jobs="jobs"></jobs-list>
    </body>
  </div>
</template>

<script>
import FilterBar from './components/FilterBar.vue'
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
    "filter-bar": FilterBar
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

#filter-bar {
  overflow: hidden;
  position: fixed;
  top: 80px;
  height: 100vh;
  width: 20%;
  transition: 0.3s;
  z-index: 9;
  margin-top: 0;
}

body {
  display: inline-block;
  position: relative;
  margin-left: 150px;
  padding-left: 0;
  top:60px;

  width: 100%;
}

</style>
