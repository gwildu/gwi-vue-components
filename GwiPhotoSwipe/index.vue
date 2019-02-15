<template>
  <div class="gwi-photoswipe">
    <div class="pswp"></div>
    <GwiGallery images="{{thumbnails}}" />
  </div>
</template>

<script>
import GwiGallery from '../GwiGallery'
export default {
  name: "GwiPhotoSwipe",
  components: ['GwiGallery'],
  props: {
    slides: {
      type: Array
    }
  },
  computed: {
    thumbnails() {
      return slides.map(slide => ({src: slide.thumbnail, alt: slide.alt}))
    }
  }
}
</script>

<style scoped>

</style>
