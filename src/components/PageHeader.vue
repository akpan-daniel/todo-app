<script>
import { useDark } from "@vueuse/core";

export default {
  data() {
    return {
      isDark: useDark(),
    };
  },
};
</script>

<template>
  <section class="absolute h-[300px] -z-10">
    <img
      v-if="isDark"
      class="w-full block h-full bg-no-repeat object-fit object-left"
      src="/assets/images/bg-desktop-dark.jpg"
      alt="header bg"
    />
    <img
      v-else
      class="w-full block h-full bg-no-repeat object-fit object-left"
      src="/assets/images/bg-desktop-light.jpg"
      alt="header bg"
    />
  </section>
</template>
