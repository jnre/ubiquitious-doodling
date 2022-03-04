<script setup lang="ts">
import { onMounted, ref } from "vue";
const router = useRouter();

const navLinks = router.getRoutes();

console.log(navLinks);

definePageMeta({
  layout:"custom",
});
</script>

<template>
  <div>
    <h1>home</h1>
    <ul>
      <li v-for="link in navLinks" :key="link.id" class="mr-4">
        <nuxt-link :to="link.path">{{ link.name }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<style></style>
