<template lang="html">

</template>

<script>
export default {
  name: 'app',
  data(){
    return{
      jobs: []
    }
  },
  mounted(){
    fetch('https://jobs.github.com/positions.json?description=javascript&location=europe')
    .then(res => res.json())
    .then(jobs => this.jobs = jobs)
  }
}
</script>

<style lang="css" scoped>
</style>
