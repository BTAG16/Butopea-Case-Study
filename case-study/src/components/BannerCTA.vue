<script setup>
  const props = defineProps({
    item: { type: Object, required: true }
  });
</script>

<template>
  <a :href="props.item.link || '#'" class="cta-root aspect-square" target="_blank">
    <div class="cta-inner">
      <h3 class="cta-title">{{ props.item.title }}</h3>
      <button class="cta-button" type="button">{{ props.item.button }}</button>
    </div>
  </a>
</template>

<style scoped>
.cta-root {
  display:block;
  background: var(--cta-bg);
  color: var(--cta-text);
  border-radius: 8px;
  text-decoration: none;
  overflow: hidden;
}

.cta-inner {
  position: absolute;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  padding: 12px;
}

.cta-title { margin:0; font-size:18px; text-align:center; }
.cta-button {
  margin-top:10px;
  padding:8px 14px;
  border:none;
  border-radius:6px;
  cursor:pointer;
  background: rgba(0,0,0,0.12);
  color: inherit;
}

@media (max-width: 767px){
  .cta-root { aspect-ratio: auto; height: 80px; border-radius:8px; }
  .cta-inner { align-items:flex-start; padding:12px; display:flex; justify-content:center; gap:12px; }
  .cta-title { font-size:16px; color:#111; }
  .cta-button { background:#111; color:#fff; }
}
</style>
