<template lang="html">
  <div>
    <header>
      <h1>DevJobs.com</h1>
      <search-form :jobs="jobs"/>
    </header>
    <body>
      <jobs-list :jobs="jobs"></jobs-list>
    </body>
  </div>
</template>

<script>
import SearchForm from './components/SearchForm.vue'
import JobsList from './components/JobsList.vue'
import JobsListItem from './components/JobsListItem.vue'
export default {
  name: 'app',
  data(){
    return{
      jobs: [],
      // password: {'Authorization': '1fa69c49-16e8-4448-bc6c-c84e38793d6c'}
    }
  },
  mounted(){
    fetch('https://jobs.github.com/positions.json?')
    // fetch('https://www.reed.co.uk/api/1.0/search?', password)
    .then(res => res.json())
    .then(jobs => this.jobs = jobs)
  },
  components:{
    "jobs-list": JobsList,
    "jobs-list-item": JobsListItem,
    "search-form": SearchForm
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
