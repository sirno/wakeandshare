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
@import ../styles/colors
@import ../styles/font

#session-input-time
  width: 25rem
  @media #{$small-query}
    width: 15rem
input
  background-color: $white
  border: 0.2rem solid $pink
  -webkit-box-shadow: 0.2rem 0.2rem 0.2rem $pink
  box-shadow: 0.2rem 0.2rem 0.2rem $pink
  &[type="number"]
    font-size: $font-size-input
    font-weight: 700

input:focus
  background-color: $yellow
  border: 0.2rem solid $blue
  -webkit-box-shadow: 0.2rem 0.2rem 0.2rem $blue
  box-shadow: 0.2rem 0.2rem 0.2rem $blue
</style>
