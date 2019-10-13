<template lang="html">
  <div id="search-filter">
    <label for="input-box">Filter Jobs by Location: </label>
    <input id="input-box" type="text" v-model="searchQuery" v-on:keyup="searchJobs" placeholder="Seach jobs by location...">
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'search-filter',
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
</style>
