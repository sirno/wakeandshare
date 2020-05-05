<template>
  <div id="session">
    <ul id="costs-list">
      <li v-for="(rider, index) in store.state.riders" :key="index">
        <pre>{{ Math.round((totalPrice * rider.time) / totalTime) }}</pre>
      </li>
    </ul>
    <br />
    <hr />
    {{ store.state.sessionTime }}
    X {{ store.state.multiplier }} + {{ uniqueRiders }} = {{ totalPrice }}
  </div>
</template>

<script>
export default {
  name: "Session",
  props: {
    store: Object,
  },
  computed: {
    totalTime: function() {
      return this.store.state.riders.reduce(
        (prev, ride) => prev + ride.time,
        0
      );
    },
    uniqueRiders: function() {
      return this.store.state.riders.reduce(
        (acc, val, idx, arr) => (acc += arr.indexOf(val) === idx ? 1 : 0),
        0
      );
    },
    timePrice: function() {
      return this.store.state.sessionTime * this.store.state.multiplier;
    },
    totalPrice: function() {
      return this.timePrice + this.uniqueRiders;
    },
  },
};
</script>

<style lang="sass" scoped>
@import "../styles/colors.sass"
hr
  border: 2px solid $blue
ul
  list-style-type: none
</style>
