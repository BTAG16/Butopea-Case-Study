<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';
import BannerImage from './BannerImage.vue';
import BannerCTA from './BannerCTA.vue';

const props = defineProps({
  mode: { type: String, default: 'square' }, 
  carouselOnMobile: { type: Boolean, default: false },
  items: { type: Array, required: true } 
});

const isMobile = ref(false);
let mq;
onMounted(() => {
  mq = window.matchMedia('(max-width: 767px)');
  isMobile.value = mq.matches;
  const handler = (e) => (isMobile.value = e.matches);
  if (mq.addEventListener) mq.addEventListener('change', handler);
  else mq.addListener(handler);
  onUnmounted(() => {
    if (mq.removeEventListener) mq.removeEventListener('change', handler);
    else mq.removeListener(handler);
  });
});

const rectImage = computed(() => props.items.find(i => i.type === 'image' && i.aspectRatio === 'rectangle'));
const squareImage = computed(() => props.items.find(i => i.type === 'image' && i.aspectRatio === 'square'));
const ctaItem = computed(() => props.items.find(i => i.type === 'cta'));

const imageItems = computed(() => props.items.filter(i => i.type === 'image' && i.aspectRatio === 'square'));
const boxesInOrder = computed(() => props.items);

const carouselRef = ref(null);
function scrollToSlide(index) {
  const el = carouselRef.value;
  if (!el) return;
  const slide = el.children[index];
  if (slide) slide.scrollIntoView({ behavior: 'smooth', inline: 'start' });
}
</script>

<template>
  <div class="banner-component">
    <div v-if="props.mode === 'square'">
      <div v-if="props.carouselOnMobile && isMobile" class="carousel-area">
        <div ref="carouselRef" class="carousel-wrapper">
          <div v-for="(it, i) in imageItems" :key="i" class="carousel-slide aspect-square">
            <a :href="it.link || '#'" target="_blank">
              <img :src="it.src" :alt="it.alt || ''" class="fill-img" loading="lazy" />
            </a>
          </div>
        </div>

        <div class="carousel-thumbs">
          <button v-for="(it, idx) in imageItems" :key="idx" class="thumb-btn" @click="scrollToSlide(idx)">
            <img :src="it.src" :alt="it.alt || ''" class="fill-img" />
          </button>
        </div>
      </div>

      <div v-show="!(props.carouselOnMobile && isMobile)" class="grid-wrapper grid-3">
        <div v-for="(item, idx) in boxesInOrder" :key="idx" class="grid-item">
          <component :is="item.type === 'image' ? BannerImage : BannerCTA" :item="item" />
        </div>
      </div>
    </div>

    <div v-else-if="props.mode === 'rectangle'">
      <div v-if="!isMobile && rectImage" class="rect-desktop" :style="{ backgroundImage: `url(${rectImage.src})` }">
        <template v-if="ctaItem">
          <a :href="ctaItem.link || '#'" class="rect-cta" target="_blank">
            <div class="rect-cta-inner">
              <h3>{{ ctaItem.title }}</h3>
              <button class="rect-btn">{{ ctaItem.button }}</button>
            </div>
          </a>
        </template>
      </div>

      <div v-else class="rect-mobile">
        <div v-if="squareImage" class="mobile-square aspect-square">
          <a :href="squareImage.link || '#'" target="_blank">
            <img :src="squareImage.src" :alt="squareImage.alt || ''" class="fill-img" loading="lazy" />
          </a>
        </div>
        <div v-if="ctaItem" class="mobile-cta">
          <a :href="ctaItem.link || '#'" class="mobile-cta-link" target="_blank">
            <div class="mobile-cta-inner">
              <div>
                <h3 style="margin:0">{{ ctaItem.title }}</h3>
              </div>
              <div>
                <button class="mobile-btn">{{ ctaItem.button }}</button>
              </div>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .grid-wrapper { margin-top: 12px; }

  .carousel-wrapper {
    display:flex;
    overflow-x:auto;
    scroll-snap-type: x mandatory;
    -webkit-overflow-scrolling: touch;
    gap: 12px;
    padding-bottom: 8px;
    margin-bottom: 8px;
  }
  .carousel-slide {
    min-width: 100%;
    scroll-snap-align: start;
    flex: 0 0 100%;
    border-radius: 8px;
    overflow:hidden;
  }

  .carousel-thumbs { display:flex; gap:8px; }
  .thumb-btn {
    width:64px; height:64px; padding:0; border:none; background:transparent; border-radius:6px; overflow:hidden;
  }

  .rect-desktop {
    height: 320px;
    background-size: cover;
    background-position: center;
    border-radius: 8px;
    position: relative;
    overflow: hidden;
    margin-top: 12px;
  }
  .rect-cta {
    position: absolute;
    right: 16px;
    bottom: 16px;
    background: #ffffffd8;
    border-radius: 10px;
    padding: 5px;
    color: #111;
  }
  
  .rect-cta-inner { display:flex; flex-direction: column; align-items:center; justify-content:space-between; width: 300px;}
  .rect-btn { background:#111; color:#fff; border:none; padding:8px 10px; border-radius:6px; }

  .mobile-cta { background:#fff; padding:12px; margin-top:12px; border-radius:8px; }
  .mobile-cta-link { color:#111; display:block; }
  .mobile-cta-inner { display:flex; justify-content:space-between; align-items:center; gap:12px; }

  a:focus { outline: 2px solid #4d90fe; outline-offset: 2px; }

</style>