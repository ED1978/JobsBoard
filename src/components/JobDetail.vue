<template lang="html">
  <div v-if="job">
    <h3>Vacancy Details:</h3>
    <h4>Date Posted: {{job.created_at}}</h4>
    <h4>Description</h4>
    <p v-html="job.description"></p>
    <h3>How to apply:</h3>
    <p v-html="job.how_to_apply"></p>
    <button v-on:click="closeClicked" type="button" name="button">Close</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'job-detail',

  props: ['job'],

  methods: {
    closeClicked(){
      eventBus.$emit('close-details');
    }
  }

}
</script>

<style lang="css" scoped>
button {
  margin-right: 15px;
}
</style>
