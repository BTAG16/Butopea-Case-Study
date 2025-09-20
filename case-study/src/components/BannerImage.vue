<script setup>
  const props = defineProps({
    item: { type: Object, required: true }
  });
</script>

<template>
  <a :href="props.item.link || '#'" target="_blank" class="aspect-square">
    <img :src="props.item.src" :alt="props.item.alt || ''" class="fill-img" loading="lazy" />
  </a>
</template>

<style scoped>

</style>
