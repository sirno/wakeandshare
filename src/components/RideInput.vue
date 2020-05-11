<template>
  <div id="ride-input">
    <form @submit.prevent>
      <input id="ride-input-rider" type="text" v-model="ride.rider" placeholder="NAME" />
      <input id="ride-input-time" type="number" v-model.number="ride.time" />
      <input type="submit" @click="onSubmit()" value="Submit" />
    </form>
  </div>
</template>

<script>
export default {
  name: "RideInput",
  data: function() {
    return {
      ride: {
        rider: "",
        time: 0
      }
    };
  },
  props: ["store"],
  methods: {
    onSubmit: function() {
      console.log(this.ride);
      if (this.ride.rider.length == 0) return;
      if (this.ride.time < 1) return;
      this.store.addRide(this.ride);
      this.ride = {
        rider: "",
        time: 0
      };
    }
  }
};
</script>

<style lang="sass" scoped>
@import ../styles/colors
@import ../styles/font
@import ../styles/mixins

#ride-input-name
  width: 8rem
#ride-input-time
  width: 4rem

input
  margin: 0.5rem
  background-color: $white
  border: 0.2rem solid $pink
  +shadow(0.2rem, $pink)
  &[type="submit"]
    border: 0.2rem solid $green
    box-shadow: none
    font-size: $font-size-input
    font-weight: $font-stack-weight
  &[type="text"]
    font-size: $font-size-input
    font-weight: $font-stack-weight
  &[type="number"]
    font-size: $font-size-input
    font-weight: $font-stack-weight
    --moz-appearance: textfield
    :-webkit-outer-spin-button:
      --webkit-appearance: none
      margin: 0
    :-webkit-inner-spin-button:
      --webkit-appearance: none
      margin: 0
input:focus
  background-color: $yellow
  border: 0.2rem solid $blue
  +shadow(0.2rem, $blue)
</style>
