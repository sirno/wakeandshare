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
      this.store.addRider(this.ride);
      this.ride = {};
    },
  },
};
</script>

<style lang="sass" scoped>
@import "../styles/colors.sass"

#ride-input-name
  width: 50px

#ride-input-time
  width: 25px

input
  margin: 5px
  background-color: $white
  border: 2px solid $pink
  -webkit-box-shadow: 2px 2px 2px $pink
  box-shadow: 2px 2px 2px $pink
  &[type="submit"]
    border: 2px solid $green
    box-shadow: none
input:focus
  background-color: $yellow
  border: 2px solid $blue
  -webkit-box-shadow: 2px 2px 2px $blue
  box-shadow: 2px 2px 2px $blue
</style>
