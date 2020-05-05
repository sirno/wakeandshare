<template>
  <div id="session-input">
    <input
      id="session-input-time"
      type="number"
      v-model="sessionTime"
      @change="store.setSessionTime(sessionTime)"
    />
  </div>
</template>

<script>
export default {
  name: "sessionInput",
  props: {
    store: Object,
  },
  data: function() {
    return {
      sessionTime: this.store.state.sessionTime,
    };
  },
};
</script>

<style lang="sass" scoped>
@import "../styles/colors.sass"

input
  background-color: $white
  border: 2px solid $pink
  -webkit-box-shadow: 2px 2px 2px $pink
  box-shadow: 2px 2px 2px $pink

input:focus
  background-color: $yellow
  border: 2px solid $blue
  -webkit-box-shadow: 2px 2px 2px $blue
  box-shadow: 2px 2px 2px $blue
</style>
