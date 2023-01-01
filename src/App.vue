<script>
import PageHeader from "./components/PageHeader.vue";
import TodoHeader from "./components/Todo/TodoHeader.vue";
import TodoInput from "./components/Todo/TodoInput.vue";

export default {
  data() {
    return {
      todos: [],
    };
  },
  components: {
    PageHeader,
    TodoHeader,
    TodoInput,
  },
  mounted() {
    document.body.classList.add("bg-gray-200", "dark:bg-gray-900");
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
      console.log(this.todos);
    },
  },
};
</script>

<template>
  <main>
    <PageHeader />
    <div class="max-w-[600px] mx-auto pt-20">
      <TodoHeader />
      <TodoInput @create-todo="addTodo" />
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
