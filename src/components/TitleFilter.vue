<template lang="html">
  <div id="title-filter">
    <label for="input-box">Filter Jobs by Title: </label>
    <input id="input-box" type="text" v-model="searchQuery" v-on:keyup="searchJobs" placeholder="Seach jobs by Title...">
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'Title-filter',
  data(){
    return{
      searchQuery: ""
    }
  },
  props: ['jobs'],
  methods: {
    searchJobs(){
      eventBus.$emit('search-query', this.searchQuery)
    }
  }
}
</script>

<style lang="css" scoped>
#title-filter {
  display: inline-block;
  border-bottom: 1px dotted black;
  padding-bottom: 20px;
  width: auto;
}
</style>
