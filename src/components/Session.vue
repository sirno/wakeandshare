<template>
  <div id="session">
    <ul v-if="store.state.gatherFlag">
      <li v-for="(time, rider) in store.state.riders" :key="rider">
        <pre>{{ computePrice(time) }}</pre>
      </li>
    </ul>
    <ul v-else>
      <li v-for="(ride, index) in store.state.rides" :key="index">
        <pre>{{ computePrice(ride.time) }}</pre>
      </li>
    </ul>
    <br />
    <hr />
    {{ store.state.sessionTime }}
    X {{ store.state.multiplier }} + {{ uniqueRiders }} =
    {{ Math.round(totalPrice) }}
  </div>
</template>

<script>
export default {
  name: "Session",
  props: {
    store: Object
  },
  computed: {
    totalTime: function() {
      return this.store.state.rides.reduce((prev, ride) => prev + ride.time, 0);
    },
    uniqueRiders: function() {
      return Object.keys(this.store.state.riders).length;
    },
    timePrice: function() {
      return this.store.state.sessionTime * this.store.state.multiplier;
    },
    totalPrice: function() {
      return this.timePrice + this.uniqueRiders;
    }
  },
  methods: {
    computePrice(time) {
      return Math.round((this.totalPrice * time) / this.totalTime);
    }
  }
};
</script>

<style lang="sass" scoped>
@import ../styles/colors
hr
  border: 0.2rem solid $blue
ul
  list-style-type: none
</style>
