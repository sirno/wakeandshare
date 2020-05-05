<template>
  <div class="title">
    <span class="bigger">WAKE</span>
    <span class="box-border">and</span>
    <span class="big line-around">Share</span>
  </div>
</template>

<script>
export default {
  name: "Title",
};
</script>

<style scoped>
span.bigger {
  font-size: 280%;
  padding: 0 1.1rem;
  background-color: yellow;
}

span.big {
  font-size: 200%;
  color: yellow;
  background-color: purple;
  padding: 0 1rem;
  line-height: 6.4rem;
}

span.box-border {
  font-size: 89%;
  color: purple;
  padding: 0.3rem 0.6rem 0.3rem 0.5rem;
  border: 0.3rem solid var(--greenColor);
}

span.line-around {
  font-size: 150%;
  color: black;
  margin: 0;
  padding: 0 0.6rem 0 0.5rem;
  background-color: white;
  border: 0.3rem solid black;
}
</style>
