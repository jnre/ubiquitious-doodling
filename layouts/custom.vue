<script setup lang="ts">
import { ref, onMounted } from "vue";
    const isVisible = ref(false);
    const toggleVisibility = () => {
      isVisible.value = !isVisible.value;
    };
const navItems = [
    {
        name: "Home",
        link: "/",
        icon: () => import("~assets/svgs/home.svg")
    },
    {
        name: "Shorts",
        link: "/shorts",
        icon: () => import("~assets/svgs/rocket.svg"),
    },
	{
        name: "About",
        link: "/about",
        icon: () => import("~assets/svgs/about.svg")
	}
];
const socialItems = [
    {
        name: "Twitter",
        link: 'www.twitter.com',
        icon: () => import("~assets/svgs/twitter.svg")
    },
    {
        name: "Github",
        link: 'www.github.com',
        icon: () => import("~assets/svgs/github.svg")
    },
    {
        name: "Linkedin",
        link: 'www.linkedin.com',
        icon: () => import("~assets/svgs/linkedin.svg")
    }
];
</script>
<template>
    <nav id="navigation"
    class="bg-white px-6 py-4 md:py-8 sticky top-0 z-40 font-body shadow-card hover:shadow-cardhover transition-all duration-500">
<!-- Container to give Navbar a fixed width -->
    <div class="flex mx-auto items-center justify-between flex-wrap p-4 max-w-7xl">
        
      <!-- Logo Icon -->
      <NuxtLink to="/" class="flex items-center flex-no-shrink">
        <BrandLogo class="h-9" alt="limosyn.com" title="Go Home" />
      </NuxtLink>
        
      <!-- Icons that show up on mobile or when window width is less -->
      <span class="flex md:hidden items-center flex-row">
        <a v-for="icon in socialItems" :key="item.name" target="_blank" :href="icon.link" :title="icon.name1" rel="noopener" >
          <component :is="icon.icon" class="h-6 w-6 ml-4 text-gray-200 hover:text-white" />
        </a>
      </span>
        
      <!-- Collapsable Menu Button - if one is active other is not. -->
      <div class="block md:hidden">
        <button type="button" class="inline-flex items-center justify-center border p-1 rounded text-gray-400 border-gray-400 hover:border-white focus:border-white hover:text-white focus:text-white focus:outline-none" aria-controls="mobile-menu" aria-expanded="false" @click="toggleVisibility">
          <span class="sr-only">Open main menu</span>
            
          <!-- Burger button svg-->
          <svg v-if="!isVisible" class="block h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
            
          <!-- Cross button svg -->
          <svg v-if="isVisible" class="block h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
        
      <!-- Items of collapsible menu -->
      <div :class="{ hidden: !isVisible }" class="w-full text-lg font-medium text-gray-200 hover:text-white flex-grow md:flex md:items-center md:w-auto md:ml-10">
        <span v-for="menu in navItems" :key="menu.name" class="flex flex-row mt-6 md:mt-0 mr-6"> <NuxtLink :to="menu.link" class="flex items-center no-underline flex-row" @click.native="toggleVisibility" >
          <component :is="menu.icon" class="w-5 h-5 mr-2 ml-1" /> \{\{ item.name }} </NuxtLink>
        </span>
        <!-- Icons that show up when window width > md(768px) -->
        <span class="hidden md:flex flex-row mt-4 md:mt-0 ml-auto">
          <a v-for="icon in socialItems" :key="icon.name" target="_blank" :href="icon.link" :title="item.name" rel="noopener" >
          	<component :is="icon.icon" class="h-6 w-6 ml-4" />
          </a>
        </span>
      </div>
    </div>
  </div>
</template>
