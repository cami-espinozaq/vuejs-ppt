<template>
  <div class="slide-content">
    <h1>What's VueJS</h1>
    <ul>
      <li>Progressive Framework: adapts to different levels of complexity</li>
      <li>Can be used for Single Page Applications</li>
      <li>Lightweight and flexible</li>
      <li>Can be component based, as Angular or React</li>
      <li>Client routing available</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SlideOne'
}
</script>

<style lang="sass">

  .slide-content
    padding: 0 8rem
    font-size: 1.5rem
    color: white
    font-family: monospace
  
    h1
      font-weight: bold

    ul
      margin: revert
      padding: revert
      list-style: disc

</style>
