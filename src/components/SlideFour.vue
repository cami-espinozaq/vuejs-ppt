<template>
  <div class="slide-content">
    <img class="full-page-img" :src="compareImg" />
  </div>
</template>

<script>
import compareImg from '../assets/images/options-vs-composition.png';

export default {
  name: 'SlideFour',
  data: () => {
    return {
      compareImg,
    };
  },
};
</script>

<style lang="sass">
.full-page-img
  max-width: 80%
  margin: auto
  display: block
  margin-top: 2rem
</style>
