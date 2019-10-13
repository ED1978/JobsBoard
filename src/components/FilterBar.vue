<template lang="html">
  <div id="filter-bar">
    <div id="title-filter">
      <Title-filter/>
    </div>
  </div>
</template>

<script>
import TitleFilter from './TitleFilter.vue'
export default {
  name: 'filter-bar',
  components: {
    "Title-filter": TitleFilter
  }
}
</script>

<style lang="css" scoped>
#filter-bar {
  border-right: 1px solid black;
  width: 100px;
  height: 100%;
}

#title-filter {
  position: relative;
  top: 15px;
  left: 5px;
}
</style>
