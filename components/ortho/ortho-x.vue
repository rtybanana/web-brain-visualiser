<template>
  <svg ref="axes" id="axes" width="100%" version="1.1" viewBox="0 0 187.2 165.6" xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink">
    <image width="187.2" height="165.6" href="./brainaxes/x.svg" opacity="0.65"/>
  </svg>
</template>

<script>
  // import { OrthoMixin } from '/mixins/ortho.js';

  module.exports = {
    mixins: [OrthoMixin],
    data: function () {
      return {
        scale: 0.9547452,
        offset: [107.366696, 88.754628]
      };
    }
  };
</script>

<style scoped>
#axes {
  overflow: visible;
}
</style>