<template lang="html">
  <div v-if="job">
    <h3>Date Posted: {{job.created_at}}</h3>
    <h3>Description</h3>
    <p>{{job.description}}</p>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'job-detail',

  props: ['job']

}
</script>

<style lang="css" scoped>
</style>
