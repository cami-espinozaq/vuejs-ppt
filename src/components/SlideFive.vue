<template>
  <div class="slide-content full-screen">
    <iframe
      src="https://codesandbox.io/embed/wonderful-mccarthy-ikb69?fontsize=14&hidenavigation=1&theme=dark"
      style="width:100%; height:80%; border:0; border-radius: 4px; overflow:hidden;"
      title="wonderful-mccarthy-ikb69"
      allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
      sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
    ></iframe>
  </div>
</template>

<script>
export default {
  name: 'SlideFive',
};
</script>

<style lang="sass">
.slide-content
  &.full-screen
    height: 100%
    display: flex
    align-items: center
</style>
