<template>
  <div id="riders-component">
    <ul id="riders-list">
      <li v-for="(rider, index) in store.state.riders" :key="index">
        <pre>{{ rider.name }}&#9;{{ rider.time }}</pre>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Riders",
  props: ["store"],
};
</script>

<style lang="sass" scoped>
ul
  list-style-type: none
</style>
