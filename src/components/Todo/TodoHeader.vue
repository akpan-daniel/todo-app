<script setup>
import { useDark, useToggle } from "@vueuse/core";

const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>

<template>
  <div class="flex justify-between">
    <h1 class="font-semibold text-white text-3xl tracking-[18px]">TODO</h1>
    <button @click="toggleDark()">
      <img
        v-if="isDark"
        src="/assets/images/icon-moon.svg"
        alt="switch theme"
      />
      <img v-else src="/assets/images/icon-sun.svg" alt="switch theme" />
    </button>
  </div>
</template>
