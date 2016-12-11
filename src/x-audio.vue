<template>
  <div id="audio">
    <audio :src="audioSrc" autoplay controls>
      您的瀏覽器不支援 audio 標籤功能。
    </audio>
  </div>
</template>
<script>
export default {
  name: 'x-audio',
  props: {
    audioSrc: String,
  },
  data() {
    return {}
  },
  computed: {}
}
</script>
<style>
</style>
