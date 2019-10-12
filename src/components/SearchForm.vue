<template lang="html">
  <form v-on:submit.prevent>

  </form>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'search-form',
  data(){
    return{
      search: "",
      selectedJob: null
    }
  },
  props: ['jobs']
}
</script>

<style lang="css" scoped>
</style>
