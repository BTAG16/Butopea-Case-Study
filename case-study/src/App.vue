<script setup>
import BannerComponent from './components/BannerComponent.vue';
import './styles/globals.css';

const squareItems1 = [
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link1' },
  { type:'cta', title:'CTA Title', button:'CTA Button', link:'https://example.com/link2' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link3' }
];

const squareItems2 = [
  { type:'cta', title:'CTA Title', button:'CTA Button', link:'https://example.com/link1' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link2' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link3' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link3' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link3' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link3' },
];

const rectItems = [
  { type:'image', aspectRatio:'rectangle', src:'https://picsum.photos/1200/400', link:'https://example.com/link1' },
  { type:'image', aspectRatio:'square', src:'https://picsum.photos/400', link:'https://example.com/link1' },
  { type:'cta', title:'CTA Title', button:'CTA Button', link:'https://example.com/link1' }
];
</script>

<template>
  <main class="container">
    <BannerComponent mode="square" :carouselOnMobile="false" :items="squareItems1" />
    <br>
    <BannerComponent mode="square" :carouselOnMobile="true" :items="squareItems2" />
    <br>
    <BannerComponent mode="rectangle" :carouselOnMobile="false" :items="rectItems" />
  </main>
</template>

<style>
</style>
