<template>
    <div :id="id">
        <div :class="'close-' + id"> 
            <div class="close-container">
              <div class="leftright"></div>
              <div class="rightleft"></div>
              <!-- <label class="close">close</label> -->
            </div>
          </div>
        <div class="modal-content">
            <iframe :src="url"></iframe>
        </div>
    </div>
</template>
<script setup>
  const props = defineProps(["id", "url"]);
</script>
<style>
 iframe {
  width: 100%;
  height: calc(100vh - 72px);
 }
</style>