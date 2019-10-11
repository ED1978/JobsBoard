<template lang="html">
  <div id="jobs-list-item">
    <h3>{{job.type}} <span>{{job.title}}</span></h3>
    <h4>{{job.company}}</h4>
    <p>{{job.location}}</p>
    <img v-bind:src="job.company_logo" alt="Companylogo">
  </div>
</template>

<script>
export default {
  name: 'jobs-list-item',
  props: ['job']

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
