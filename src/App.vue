<template>
  <Renderer resize="window">
    <Camera :position="{ z: 100 }" />
    <Scene>     
      <Box :size="10">
        <BasicMaterial />
      </Box>
    </Scene>
  </Renderer>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { Box, Camera, MeshPublicInterface, Renderer, RendererPublicInterface, Scene } from 'troisjs'

const rendererC = ref()
const meshC = ref()

onMounted(() => {
  const renderer = rendererC.value as RendererPublicInterface
  const mesh = (meshC.value as MeshPublicInterface).mesh
  renderer.onBeforeRender(() => {
    mesh!.rotation.x += 0.01
  })
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
