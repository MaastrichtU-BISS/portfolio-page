<template>
  <div class="container">
    <div class="background-images">
      <img src="./assets/img/biss_um_logo.png" id="biss-logo" />
      <img src="./assets/img/hexagon.png" class="hexagon" />
    </div>
    <div class="row">
      <Title/>
    </div>
    <div class="row">
      <div class="cards-list">
        <Card :id="'card-au2s'" :title="'Audio to Semantics'" :url="'#au2s'" :img_url="'/src/assets/img/au2sem.gif'"/>
        <Card :id="'card-proj-ov'" :title="'Our Projects'" :url="'#proj-ov'" :img_url="'/src/assets/img/projects.gif'"/>
        <Card :id="'card-txt2img'" :title="'Text to Images'" :url="'#txt2img'" :img_url="'/src/assets/img/dalle.gif'"/>
      </div>
    </div>
    <div class="row fixed-bottom" style="padding: 0 .5rem;">
      <h2>*BISS is like the A-team, but with professors from Maastricht University</h2>
    </div>
    <div>
      <InnerModal :id="'au2s'" :url="'http://localhost:3001'"/>
      <InnerModal :id="'proj-ov'" :url="'http://localhost:3000'"/>
      <InnerModal :id="'txt2img'" :url="'http://localhost:3002'"/>
    </div>
  </div>
</template>

<script setup>
import Title from "./components/Title.vue";
import Card from "./components/Card.vue"
import InnerModal from "./components/InnerModal.vue"
import {onMounted} from 'vue';

onMounted(()=>{
  const options = { color: '#009EE3'};
  $("#card-au2s").animatedModal(options);
  $("#card-proj-ov").animatedModal(options);
  $("#card-txt2img").animatedModal(options);
})

</script>
<style>
@import "../src/assets/css/animate.min.css";
@import "../src/assets/css/close-modal.css";
@import "../src/assets/css/cards.css"
</style>
