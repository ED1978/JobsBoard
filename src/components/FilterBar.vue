<template lang="html">
  <div id="filter-bar">
    <div class="filter-input">
      <Title-filter :jobs="jobs"/>
    </div>
    <div class="filter-input">
      <location-filter :jobs="jobs"/>
    </div>
  </div>
</template>

<script>
import TitleFilter from './TitleFilter.vue'
import LocationFilter from './LocationFilter.vue'
export default {
  name: 'filter-bar',
  components: {
    "Title-filter": TitleFilter,
    "location-filter": LocationFilter
  },
  props: ['jobs']
}
</script>

<style lang="css" scoped>
#filter-bar {
  /* border-right: 1px solid black; */
  width: 100px;
  height: 100%;
}

.filter-input {
  position: relative;
  top: 25px;
  left: 5px;
}
</style>
