<template>
  <div id="session-input">
    <input
      id="session-input-time"
      type="text"
      pattern="\d*"
      inputmode="numeric"
      v-model.number="sessionTime"
      @change="store.setSessionTime(sessionTime)"
    />
  </div>
</template>

<script>
export default {
  name: "sessionInput",
  props: {
    store: Object
  },
  data: function() {
    return {
      sessionTime: this.store.state.sessionTime
    };
  }
};
</script>

<style lang="sass" scoped>
@import ../styles/colors
@import ../styles/font
@import ../styles/mixins

#session-input-time
  width: 25rem
  @media #{$small-query}
    width: 15rem
input
  background-color: $white
  border: 0.2rem solid $pink
  +shadow(0.2rem, $pink)
  &[type="text"]
    font-size: $font-size-input
    font-weight: 700
    @media #{$small-query}
      font-size: $font-size-small
input:focus
  background-color: $yellow
  border: 0.2rem solid $blue
  +shadow(0.2rem, $blue)
</style>
