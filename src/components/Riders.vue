<template>
  <div id="riders-component">
    <ul v-if="store.state.gatherFlag">
      <li v-for="(time, rider) in store.state.riders" :key="rider">
        <pre>{{ rider }}&#9;{{ time }}</pre>
      </li>
    </ul>
    <ul v-else>
      <li v-for="(ride, index) in store.state.rides" :key="index">
        <pre>{{ ride.rider }}&#9;{{ ride.time }}</pre>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Riders",
  props: ["store"]
};
</script>

<style lang="sass" scoped>
ul
  list-style-type: none
</style>
