<template>
  <div id="settings">
    <p>
      Merge them
      <Checkbox
        @toggled="store.toggleGatherFlag()"
        :checked="store.state.gatherFlag"
      />
    </p>
  </div>
</template>

<script>
import Checkbox from "./Checkbox.vue";
export default {
  name: "Settings",
  components: {
    Checkbox,
  },
  props: {
    store: Object,
  },
  data: function() {
    return {
      gatherFlag: this.store.state.gatherFlag,
    };
  },
};
</script>

<style lang="sass" scoped>
#settings
  text-align: right
  font-size: 2rem
</style>
