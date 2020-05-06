<template>
  <div id="ride-input">
    <form @submit.prevent>
      <input
        id="ride-input-name"
        type="text"
        v-model="ride.name"
        placeholder="NAME"
      />
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
        name: "",
        time: 0,
      },
    };
  },
  props: ["store"],
  methods: {
    onSubmit: function() {
      console.log(this.ride);
      if (this.ride.name.length == 0) return;
      if (this.ride.time < 1) return;
      this.store.addRider(this.ride);
      this.ride = {
        name: "",
        time: 0,
      };
    },
  },
};
</script>

<style lang="sass" scoped>
@import ../styles/colors
@import ../styles/font

#ride-input-name
  width: 8rem
#ride-input-time
  width: 4rem

input
  margin: 0.5rem
  background-color: $white
  border: 0.2rem solid $pink
  -webkit-box-shadow: 0.2rem 0.2rem 0.2rem $pink
  box-shadow: 0.2rem 0.2rem 0.2rem $pink
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
input:focus
  background-color: $yellow
  border: 0.2rem solid $blue
  -webkit-box-shadow: 0.2rem 0.2rem 0.2rem $blue
  box-shadow: 0.2rem 0.2rem 0.2rem $blue
</style>
