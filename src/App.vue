<script>
import { useDark } from "@vueuse/core";

import PageHeader from "./components/PageHeader.vue";
import TodoHeader from "./components/Todo/TodoHeader.vue";

export default {
  data() {
    return {
      isDark: useDark(),
    };
  },
  components: {
    PageHeader,
    TodoHeader,
  },
  mounted() {
    document.body.classList.add("bg-gray-200", "dark:bg-gray-900");
  },
};
</script>

<template>
  <main>
    <PageHeader :isDark="isDark" />
    <div class="max-w-[600px] mx-auto pt-20">
      <TodoHeader />
    </div>
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@400;700&display=swap");
main {
  font-family: "Josefin Sans", sans-serif;
  font-weight: 400;
}
</style>
