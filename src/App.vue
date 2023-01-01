<script>
import PageHeader from "./components/PageHeader.vue";
import TodoHeader from "./components/Todo/TodoHeader.vue";
import TodoInput from "./components/Todo/TodoInput.vue";
import TodoItem from "./components/Todo/TodoItem.vue";

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
    TodoItem,
  },
  mounted() {
    document.body.classList.add("bg-gray-100", "dark:bg-gray-900");
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
      console.log(this.todos);
    },
    toggleTodo(id) {
      console.log(id);
      this.todos.forEach((todo) => {
        if (todo.id === id) {
          todo.isComplete = !todo.isComplete;
        }
      });
    },
    removeTodo(todo) {
      let index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
  },
};
</script>

<template>
  <main>
    <PageHeader />
    <section class="max-w-[600px] mx-auto pt-20">
      <TodoHeader />
      <TodoInput @create-todo="addTodo" />
      <div class="mt-[25px] shadow-lg bg-transparent">
        <TodoItem
          v-for="todo in todos"
          :key="todo.id"
          :todo="todo"
          @toggle-todo="toggleTodo"
          @remove-todo="removeTodo"
        />
      </div>
    </section>
  </main>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@400;700&display=swap");
main {
  font-family: "Josefin Sans", sans-serif;
  font-weight: 400;
}
</style>
