<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { onMounted } from 'vue';
import { EVENTS } from "./constants"
import { images } from "./data"


const setImages = () => {
  const editorElement = document.getElementById(
    "layerhub_editor_widget"
  ) as HTMLElement;
  const event = new CustomEvent(EVENTS.REQUEST_SET_DATA, {
    detail: {
      type: "SET_IMAGES",
      data: images,
    },
  });
  editorElement.dispatchEvent(event);
}

onMounted(() => {
  // LOAD WIDGET SRIPT
  const script = document.createElement("script");
  script.src = "https://xorb.github.io/design-editor-widget/index.638dd6be.js";
  script.async = true;
  script.defer = true;
  document.body.appendChild(script);

})
</script>

<template>

  <div :style="{ height: '100vh', width: '100vw', display: 'flex', flexDirection: 'column' }">
    <div :style="{
      height: '80px', backgroundColor: '#2c3e50', display: 'flex', alignItems: 'center', padding: '0.5rem'
    }">
      <button :style="{ background: '#ffffff', padding: '0.5rem 1rem' }" @click="setImages">Set images</button>
    </div>
    <div id="layerhub_editor_widget" :style="{ flex: 1 }">

    </div>
  </div>

</template>

<style scoped>

</style>
