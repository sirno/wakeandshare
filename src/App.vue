<template>
  <div id="app">
    <Title />
    <div id="top">
      <Riders v-bind:store="store" />
      <Session v-bind:store="store" />
    </div>
    <div id="input" title="input">
      <RideInput v-bind:store="store" />
      <SessionInput v-bind:store="store" />
      <Settings v-bind:store="store" />
    </div>
  </div>
</template>

<script>
import Title from "./components/Title.vue";
import Riders from "./components/Riders.vue";
import RideInput from "./components/RideInput.vue";
import Session from "./components/Session.vue";
import SessionInput from "./components/SessionInput.vue";
import Settings from "./components/Settings.vue";

var store = {
  debug: true,
  state: {
    rides: [],
    riders: {},
    sessionTime: 0,
    multiplier: 1.2,
    gatherFlag: true
  },
  addRide: function(ride) {
    if (this.debug) console.log("addRider triggered with: ", ride);
    this.state.rides.push(ride);
    this.state.riders = this.state.rides.reduce((riders, ride) => {
      riders[ride.rider] =
        ride.rider in riders ? riders[ride.rider] + ride.time : ride.time;
      return riders;
    }, {});
  },
  setSessionTime: function(time) {
    if (this.debug) console.log("setSessionTime triggered with: ", time);
    this.state.sessionTime = time;
  },
  toggleGatherFlag: function() {
    if (this.debug) console.log("toggleGatherFlag triggered");
    this.state.gatherFlag = !this.state.gatherFlag;
  }
};

export default {
  name: "App",
  components: {
    Title,
    Riders,
    RideInput,
    Session,
    SessionInput,
    Settings
  },
  data: function() {
    return {
      store: store
    };
  }
};
</script>

<style lang="sass">
@import styles/colors
@import styles/font
@import styles/imports

body
  color: $black

#app
  font-family: $font-stack
  font-weight: $font-stack-weight
  font-size: $font-size
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  margin-top: 60px
  @media #{$small-query}
    font-size: $font-size-small

#app pre
  font-family: $font-stack
  font-weight: $font-stack-weight
  font-size: $font-size
  @media #{$small-query}
    font-size: $font-size-small

#top
  display: flex
  flex-direction: row
  justify-content: center
  text-align: left

#input
  text-align: left
</style>
