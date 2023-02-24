<template>
  <a :id="id" :href="url" class="card">
    <div class="card_image"><img :src="img_url" /></div>
    <div class="card_title title-white">
      <p>{{ title }}</p>
    </div>
  </a>
</template>
<script setup>
const props = defineProps(["id", "url", "img_url", "title"]);
</script>

<style scoped>
.card_title {
  height: 130px;
}
</style>
