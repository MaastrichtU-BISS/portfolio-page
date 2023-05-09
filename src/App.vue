<template>
  <div class="container">
    <div class="background-images">
      <img src="./assets/img/biss_um_logo.png" id="biss-logo" />
      <img src="./assets/img/hexagon.png" class="hexagon" />
    </div>
    <News />
    <div class="row">
      <div class="cards-list">
        <Card
          :id="'card-au2s'"
          :title="'Geluiden herkennen'"
          :url="'#au2s'"
          :img_url="'/src/assets/img/au2sem.gif'"
          @click="stopModalTimer()"
        />
        <Card
          :id="'card-proj-ov'"
          :title="'Bekijk onze projecten'"
          :url="'#proj-ov'"
          :img_url="'/src/assets/img/projects.gif'"
          @click="stopModalTimer()"
          :class="{ press: isPressing }"
        />
        <Card
          :id="'card-txt2img'"
          :title="'Maak kunst met Kunstmatige intelligentie'"
          :url="'#txt2img'"
          :img_url="'/src/assets/img/dalle.gif'"
          @click="stopModalTimer()"
        />
      </div>
    </div>
    <div class="row fixed-bottom" style="padding: 0 0.5rem">
      <h2 class="footer_txt">
        BISS is net het A-team, maar dan met professoren van de Universiteit Maastricht
      </h2>
    </div>
    <div>
      <InnerModal @reload="reloadAudio2semantics" :id="'au2s'" :url="audio2semantics" />
      <InnerModal
        @reload="reloadProjectOverview"
        :id="'proj-ov'"
        :url="projectOverview"
      />
      <InnerModal @reload="reloadText2image" :id="'txt2img'" :url="text2image" />
    </div>
    <img
      src="./components/icons/hand_pointing.svg"
      alt=""
      class="pointing"
      v-if="countDown <= 120"
    />
  </div>
</template>

<style>
@import "../src/assets/css/animate.min.css";
@import "../src/assets/css/close-modal.css";
@import "../src/assets/css/cards.css";
</style>
<script setup>
import News from "./components/News.vue";
import Card from "./components/Card.vue";
import InnerModal from "./components/InnerModal.vue";
import { onMounted, ref, computed } from "vue";
const props = defineProps(["id", "url"]);
onMounted(() => {
  const options = { color: "#009EE3" };
  $("#card-au2s").animatedModal(options);
  $("#card-proj-ov").animatedModal(options);
  $("#card-txt2img").animatedModal(options);
  startTimer();
});

const audio2semantics = ref("http://localhost:3001");
const projectOverview = ref("http://localhost:3000");
const text2image = ref("http://localhost:3002");
let timeOut;
const countDown = ref(240);
let modalDown;
const countColseModal = ref(30 * 60);
const isPressing = computed(() => {
  return countDown.value <= 120;
});

async function reloadAudio2semantics() {
  const url = audio2semantics.value;
  audio2semantics.value = "";
  await new Promise((res) => setTimeout(res, 1 * 1000));

  audio2semantics.value = url;
  countDown.value = 240;
  startTimer();
}

async function reloadProjectOverview() {
  stopModalCount();
  const url = projectOverview.value;
  projectOverview.value = "";
  await new Promise((res) => setTimeout(res, 1 * 1000));
  projectOverview.value = url;
  countDown.value = 240;
  startTimer();
}

async function reloadText2image() {
  stopModalCount();
  const url = text2image.value;
  text2image.value = "";
  await new Promise((res) => setTimeout(res, 1 * 1000));
  text2image.value = url;
  countDown.value = 240;
  startTimer();
}

function startTimer() {
  stopModalCount();
  const timeDown = () => {
    // console.clear();
    if (countDown.value > 0) {
      console.log("seconds", countDown.value);

      timeOut = setTimeout(timeDown, 1000);
    }
    countDown.value--;
    if (countDown.value <= 0) {
      countDown.value = 240;
    }
  };
  setTimeout(timeDown, 1000);
}

function stopModalTimer() {
  clearTimeout(timeOut);
  const modalColse = () => {
    if (countColseModal.value > 0) {
      // console.log("Close the modal after ", countColseModal.value);
      modalDown = setTimeout(modalColse, 1000);
    } else {
      location.reload();
    }
    countColseModal.value--;
  };
  setTimeout(modalColse, 1000);
}
function stopModalCount() {
  clearTimeout(modalDown);
  countColseModal.value = 30 * 60;
}
</script>
