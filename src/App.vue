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
    </div>
  </div>
</template>

<script>
import Title from "./components/Title.vue";
import Riders from "./components/Riders.vue";
import RideInput from "./components/RideInput.vue";
import Session from "./components/Session.vue";
import SessionInput from "./components/SessionInput.vue";

var store = {
  debug: false,
  state: {
    riders: [],
    sessionTime: 0,
    multiplier: 1.2,
  },
  addRider(rider) {
    if (this.debug) console.log("addRider triggered with: ", rider);
    this.state.riders.push(rider);
  },
  setSessionTime(time) {
    if (this.debug) console.log("setSessionTime triggered with: ", time);
    this.state.sessionTime = time;
  },
};

export default {
  name: "App",
  components: {
    Title,
    Riders,
    RideInput,
    Session,
    SessionInput,
  },
  data: function() {
    return {
      store: store,
    };
  },
};
</script>

<style lang="sass">
@import url("https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@700&display=swap")
@import "styles/colors.sass"

$font-stack: "Roboto Mono", monospace
$font-stack-weight: 700
$font-size: 2.5rem

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

#app pre
  font-family: $font-stack
  font-weight: $font-stack-weight
  font-size: $font-size

#top
  display: flex
  flex-direction: row
  justify-content: center
  text-align: left

#input
  text-align: left
</style>
