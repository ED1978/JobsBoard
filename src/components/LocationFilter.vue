<template lang="html">
  <div id="location-filter">
    <label for="location-select">Filter Jobs by Location: </label>
    <select id="location-select" v-on:change="handleSelect" v-model="selectedJob">

    </select>
  </div>

</template>

<script>
export default {
  name: "location-filter",
  props: ['jobs'],
  data(){
    return{
      selectedJob: null
    }
  }
}
</script>

<style lang="css" scoped>
#location-filter {
  display: inline-block;
  border-bottom: 1px dotted black;
  padding-bottom: 20px;
  width: auto;
  margin-left: 20px;
  margin-top: 20px;
}
</style>
