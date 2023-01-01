<script>
import { v4 as uuid4 } from "uuid";
export default {
  emits: ["create-todo"],
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    emitTodo() {
      if (this.newTodo.length < 3) {
        return;
      }
      this.$emit("create-todo", {
        id: uuid4().toString(),
        name: this.newTodo,
        isComplete: false,
        createdAt: new Date(),
      });
      this.newTodo = "";
    },
  },
};
</script>

<template>
  <section class="bg-gray-300 dark:bg-gray-800 rounded-lg mt-12 shadow-lg">
    <form
      class="h-[65px] flex justify-center items-center"
      @submit.prevent
      @submit="emitTodo"
    >
      <input
        class="w-full h-[40px] bg-transparent border-0 outline outline-0 text-gray-700 p-[24px] placeholder:text-gray-500 dark:text-gray-300"
        v-model="newTodo"
        type="text"
        placeholder="Add New Todo"
      />
    </form>
  </section>
</template>
