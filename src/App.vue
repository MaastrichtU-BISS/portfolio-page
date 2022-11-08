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
      <ul class="grid remove-list-styling">
        <li class="placeholder">Placeholder</li>
        <li class="placeholder">Placeholder</li>
        <li class="placeholder">Placeholder</li>
        <li class="placeholder">Placeholder</li>
      </ul>
    </div>
    <div class="row fixed-bottom" style="padding: 0 .5rem;">
      <h2>*BISS is like the A-team, but with professors from Maastricht University</h2>
    </div>
  </div>
</template>

<script setup>
import Title from "./components/Title.vue";
</script>
