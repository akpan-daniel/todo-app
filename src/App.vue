<script>
import { useDark } from "@vueuse/core";

import PageHeader from "./components/PageHeader.vue";

export default {
  data() {
    return {
      isDark: useDark(),
    };
  },
  components: {
    PageHeader,
  },
  mounted() {
    document.body.classList.add("bg-gray-200", "dark:bg-gray-900");
  },
};
</script>

<template>
  <main>
    <PageHeader :isDark="isDark" />
  </main>
</template>

<style>
#todo-wrapper {
  margin-inline: auto;
}
</style>
