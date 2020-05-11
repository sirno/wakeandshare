<template>
  <div class="button" :class="{ highlighted: isHighlighted }" @click="clicked"></div>
</template>

<script>
export default {
  name: "Button",
  data: function() {
    return {
      isHighlighted: false
    };
  },
  methods: {
    clicked: function() {
      this.$emit("clicked");
      this.isHighlighted = true;
      window.setTimeout(
        function() {
          this.isHighlighted = false;
        }.bind(this),
        150
      );
    }
  }
};
</script>

<style lang="sass" scoped>
@import ../styles/colors
@import ../styles/mixins

$size: 25px
$border-size: 0.2rem

.button
  display: inline-flex
  position: relative
  flex-direction: row
  align-items: center
  justify-content: space-around
  margin-right: 2rem
  margin-left: 2rem
  width: $size
  height: $size
  border-width: $border-size
  border-style: solid
  border-color: $pink
  +shadow($border-size, $pink)
.highlighted
  background-color: $yellow
  border-color: $blue
  +shadow($border-size, $blue)
</style>