
<script setup lang="ts">
import {
  Box,
  Camera,
  PointLight,
  Renderer,
  Scene,
  BasicMaterial,
  Texture,
  AmbientLight,
} from 'troisjs';
import { onMounted, ref } from 'vue';

const renderer = ref(null);
const box = ref(null);

onMounted(() => {
  renderer?.value?.onBeforeRender(() => {
    box.value.mesh.rotation.x += 0.01;
  });
});
</script>
<template>
  <div class="ocean relative">
    <Renderer resize="window" orbit-ctrl ref="renderer" :alpha="true">
      <Camera :position="{ z: 10 }" />
      <Scene>
        <PointLight :position="{ y: 50, z: 50 }" />
        <AmbientLight />
        <Box ref="box" :rotation="{ y: Math.PI / 4, z: Math.PI / 4 }">
          <BasicMaterial>
            <Texture src="/ink.jpg" refraction :refraction-ratio="0.95" />
          </BasicMaterial>
        </Box>
      </Scene>
    </Renderer>
  </div>
</template>

<style>
.ocean {
  background-image: url('/ocean.png');
  background-size: 100% 100%;
}
</style>