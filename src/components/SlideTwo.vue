<template>
  <div class="slide-content">
    <h1>Can be used similarly to jQuery (Runtime only)</h1>
    <div class="compare">
      <img :src="imgJquery" />
      <img :src="imgVue" />
    </div>
  </div>
</template>

<script>
import imgJquery from '../assets/images/jquery.png';
import imgVue from '../assets/images/vue-simple.png';

export default {
  name: 'SlideTwo',
  data: () => {
    return {
      imgJquery: imgJquery,
      imgVue: imgVue,
    };
  },
};
</script>

<style lang="sass">

.compare
  display: flex
  align-items: center
  justify-content: space-evenly

  img
    max-width: calc(50% - 1rem)
</style>
