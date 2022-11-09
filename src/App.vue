<template>
<!-- SECTION Renderer
  // LINK https://troisjs.github.io/guide/core/renderer.html
  // LINK https://threejs.org/docs/#api/en/renderers/WebGLRenderer
  /* NOTE É o espaço aonde Three JS será renderizado para animações, no TroisJS isso é inicializado através de um componente  */
  // !SECTION -->
  <Renderer resize="window">
    <Camera :position="{ z: 100 }" :fov="75" :near="0.1" :far="1000" :aspect="aspect"/>
    <!-- SECTION Scene
    // LINK https://troisjs.github.io/guide/core/scene.html
    // LINK https://threejs.org/docs/#api/en/scenes/Scene
    // NOTE Uma cena é aonde acontece a ação do ThreeJS 
    // !SECTION -->
    <Scene ref="sceneC">     
      <Box :size="10">
        <BasicMaterial />
      </Box>
    </Scene>
  </Renderer>
</template>

<script setup lang="ts">
import { ref, onMounted, computed } from 'vue'
import { Box, Camera, MeshPublicInterface, Renderer, RendererPublicInterface, Scene, SceneInjectionKey } from 'troisjs'
import { AxesHelper, Scene as TScene } from 'three';

const sceneC = ref()
const aspect = computed(() => window.innerWidth / window.innerHeight);
onMounted(() => {
  const scene = sceneC.value as TScene
  console.dir(scene.add())
})
</script>

<style>
body, html {
  margin: 0;
}
canvas {
  display: block;
}
</style>
