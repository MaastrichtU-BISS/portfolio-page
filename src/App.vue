<template>
  <div class="container">
    <div class="background-images">
      <img src="./assets/img/biss_um_logo.png" id="biss-logo" />
      <img src="./assets/img/hexagon.png" class="hexagon" />
    </div>
    <div class="row">
      <Title />
    </div>
    <div class="row">
      <div class="cards-list">
        <a id="modal1" href="#au2s" class="card 1">
          <div class="card_image"> <img src="./assets/img/au2sem.gif"/> </div>
          <div class="card_title title-white">
            <p>Audio to Semantics</p>
          </div>
        </a>
      </div>
      <div class="cards-list">
        <a id="modal2" href="#proj-ov" class="card 2">
          <div class="card_image"> <img src="./assets/img/projects.gif"/> </div>
          <div class="card_title title-white">
            <p>Our Projects</p>
          </div>
        </a>
      </div>
      <div class="cards-list">
        <a id="modal3" href="#txt2img" class="card 3">
          <div class="card_image"> <img src="./assets/img/dolly.gif"/> </div>
          <div class="card_title title-white">
            <p>Text to Images</p>
          </div>
        </a>
      </div>
        <!-- <a id="modal1" href="#au2s">DEMO1</a>
        <a id="modal2" href="#proj-ov">DEMO2</a>
        <a id="modal3" href="#txt2img">DEMO3</a> -->
    </div>
    <div class="row fixed-bottom" style="padding: 0 .5rem;">
      <h2>*BISS is like the A-team, but with professors from Maastricht University</h2>
    </div>
    <div>
      <InnerModal :id="'au2s'" :url="'http://localhost:3001'"></InnerModal>
      <InnerModal :id="'proj-ov'" :url="'http://localhost:3000'"></InnerModal>
      <InnerModal :id="'txt2img'" :url="'http://localhost:3002'"></InnerModal>
    </div>
  </div>
</template>

<script setup>
import Title from "./components/Title.vue";
import InnerModal from "./components/InnerModal.vue"
import {ref, reactive, onMounted} from 'vue';

const selectedModal = ref(1);

onMounted(()=>{
  // { color: 'red' }
  $("#modal1").animatedModal();
  $("#modal2").animatedModal();
  $("#modal3").animatedModal();
})


</script>
<style>
@import "../src/assets/css/animate.min.css";
@import "../src/assets/css/close-modal.css";
@import "../src/assets/css/cards.css"
</style>
