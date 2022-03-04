<script setup lang="ts">
import { onMounted, ref } from "vue";
const router = useRouter();

const navLinks = router.getRoutes();

console.log(navLinks);
</script>

<template>
  <div>
    <h1>home</h1>
    <ul>
      <li v-for="link in navLinks" :key="link.id" class="mr-4">
        <NuxtLink :to="link.path">{{ link.name }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style></style>
