<template>
  <div
    class="checkbox"
    v-bind:class="{ checked: checked }"
    v-on:click="toggle()"
  ></div>
</template>

<script>
export default {
  name: "Checkbox",
  props: {
    checked: {
      type: Boolean,
      default: true,
    },
  },
  methods: {
    toggle: function() {
      this.isChecked = !this.isChecked;
      this.$emit("toggled");
    },
  },
};
</script>

<style lang="sass" scoped>
@import ../styles/colors
@import ../styles/mixins

$size: 25px
$border-size: 0.2rem

.checkbox
  display: inline-block
  margin-right: 2rem
  margin-left: 2rem
  width: $size
  height: $size
  border-width: $border-size
  border-style: solid
  border-color: $pink
  +shadow($border-size, $pink)

.checked
  background-color: $yellow
  border-color: $blue
  +shadow($border-size, $blue)
</style>
