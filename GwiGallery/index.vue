<template>
  <div>
    <!-- Root element of PhotoSwipe. Must have class pswp. -->
    <div class="pswp" tabindex="-1" role="dialog" aria-hidden="true">
      <!-- Background of PhotoSwipe.
           It's a separate element as animating opacity is faster than rgba(). -->
      <div class="pswp__bg"></div>
      <!-- Slides wrapper with overflow:hidden. -->
      <div class="pswp__scroll-wrap">
        <!-- Container that holds slides.
            PhotoSwipe keeps only 3 of them in the DOM to save memory.
            Don't modify these 3 pswp__item elements, data is added later on. -->
        <div class="pswp__container">
          <div class="pswp__item"></div>
          <div class="pswp__item"></div>
          <div class="pswp__item"></div>
        </div>
        <!-- Default (PhotoSwipeUI_Default) interface on top of sliding area. Can be changed. -->
        <div class="pswp__ui pswp__ui--hidden">
          <div class="pswp__top-bar">
            <!--  Controls are self-explanatory. Order can be changed. -->
            <div class="pswp__counter"></div>
            <button class="pswp__button pswp__button--close" title="Close (Esc)"></button>
            <button class="pswp__button pswp__button--share" title="Share"></button>
            <button class="pswp__button pswp__button--fs" title="Toggle fullscreen"></button>
            <button class="pswp__button pswp__button--zoom" title="Zoom in/out"></button>
            <!-- Preloader demo https://codepen.io/dimsemenov/pen/yyBWoR -->
            <!-- element will get class pswp__preloader--active when preloader is running -->
            <div class="pswp__preloader">
              <div class="pswp__preloader__icn">
                <div class="pswp__preloader__cut">
                  <div class="pswp__preloader__donut"></div>
                </div>
              </div>
            </div>
          </div>
          <div class="pswp__share-modal pswp__share-modal--hidden pswp__single-tap">
            <div class="pswp__share-tooltip"></div>
          </div>
          <button class="pswp__button pswp__button--arrow--left" title="Previous (arrow left)">
          </button>
          <button class="pswp__button pswp__button--arrow--right" title="Next (arrow right)">
          </button>
          <div class="pswp__caption">
            <div class="pswp__caption__center"></div>
          </div>
        </div>
      </div>
    </div>

    <div
      class="gwi-gallery"
      :style="galleryStyle"
      itemscope
      itemtype="http://schema.org/ImageGallery"
    >
      <div
        :key="`image${index}`"
        v-for="(image, index) in images"
        :style="containerStyle"
      >
        <figure
          class="figure"
          :style="figureStyle(index)"
          itemscope
          itemprop="associatedMedia"
          itemtype="http://schema.org/ImageObject"
        >
          <link rel="prefetch" :href="image.src">
          <link rel="prefetch" :href="image.msrc">
          <a
            class="link"
            @click.prevent.stopy="init(index)"
            :href="image.src"
            itemprop="contentUrl"
          >
            <GwiCard level="3" :hover-level="5" :padding="false" :margin-bottom="false">
              <img
                class="image"
                :src="image.msrc"
                itemprop="thumbnail"
                :alt="image.alt"
                :style="imgStyle"
              />
            </GwiCard>
          </a>
          <meta itemprop="width" :content="image.w" />
          <meta itemprop="height" :content="image.h" />
          <figcaption class="caption" itemprop="caption description">
            {{image.title}}
            <span itemprop="copyrightHolder">Bildhauerei Rickenbacher</span>
          </figcaption>
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
import 'photoswipe/dist/photoswipe.css'
import 'photoswipe/dist/default-skin/default-skin.css'
import PhotoSwipe from 'photoswipe/dist/photoswipe'
import PhotoSwipeDefaultUI from 'photoswipe/dist/photoswipe-ui-default'
import GwiCard from '../GwiCard/index.vue'

export default {
  name: "GwiGallery",
  components: {GwiCard},
  props: {
    images: {
      type: Array
    },
    galleryWidth: {
      type: Number,
      default() {
        return 1020
      }
    },
    maxThumbsWidth: {
      type: Number,
      default() {
        return 230
      }
    },
    maxThumbsHeight: {
      type: Number,
      default() {
        return 345
      }
    },
    thumbsPadding: {
      type: Number,
      default() {
        return 5
      }
    },
    numberOfThumbsPerRow: {
      type: Number,
      default() {
        return 4
      }
    },
    crop: {
      type: Boolean,
      default() {
        return false
      }
    },
    options: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  computed: {
    padding() {
      return (this.galleryWidth - this.numberOfThumbsPerRow * this.maxThumbsWidth) / 3
    },
    galleryStyle() {
      return {maxWidth: `${this.galleryWidth}px`}
    },
    imgStyle() {
      return this.crop ? {width: '100%', height: '100%', objectFit: 'cover'} : {}
    },
    containerStyle() {
      return {width: `${this.maxThumbsWidth + this.thumbsPadding}px`}
    }
  },
  methods: {
    init(index){
      const pswpElement = document.querySelectorAll('.pswp')[0]
      const options = {...this.options, index}
      this.gallery = new PhotoSwipe(pswpElement, PhotoSwipeDefaultUI, this.images, options)
      this.gallery.init()
    },
    figureStyle(index) {
        return {width: `${this.maxThumbsWidth}px`, margin: `0px ${(index+1) % this.numberOfThumbsPerRow === 0 ? '0px' : `${this.padding}px`} ${this.padding}px 0px`}
    }
  }

}
</script>

<style scoped lang="scss">
  @import '../theme/attributes/common/_colors.scss';

  .gwi-gallery {
    display: flex;
    flex-wrap: wrap;
    overflow: hidden;
    margin: 0 auto;
    align-items: center;
    justify-content: space-around;
  }
  .figure {
    width: 240px;
    height: 355px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .image {
    max-width: 100%;
    border: 1px solid transparent;
    padding: 5px;
  }
  .caption {
    display: none;
  }
  .link {
    max-width: 100%;
    max-height: 100%;
  }
</style>
