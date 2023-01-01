<script>
import PageHeader from "./components/PageHeader.vue";
import TodoHeader from "./components/Todo/TodoHeader.vue";
import TodoInput from "./components/Todo/TodoInput.vue";
import TodoItem from "./components/Todo/TodoItem.vue";
import TodoFilter from "./components/Todo/TodoFilter.vue";

export default {
  data() {
    return {
      todos: [],
      filter: null,
      filteredTodos: [],
    };
  },
  components: {
    PageHeader,
    TodoHeader,
    TodoInput,
    TodoItem,
    TodoFilter,
  },
  mounted() {
    document.body.classList.add("bg-gray-100", "dark:bg-gray-900");
    this.filterTodos(this.filter, this.todos);
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    toggleTodo(id) {
      console.log(id);
      this.todos = this.todos.map((todo) => {
        if (todo.id === id) {
          todo.isComplete = !todo.isComplete;
        }
        return todo;
      });
    },
    removeTodo(todo) {
      let index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
    clearCompleted() {
      this.todos = this.todos.filter((todo) => !todo.isComplete);
    },
    filterTodos(newFilter, todos) {
      if (newFilter === null) {
        this.filteredTodos = todos;
      } else if (newFilter) {
        this.filteredTodos = todos.filter((todo) => !todo.isComplete);
      } else {
        this.filteredTodos = todos.filter((todo) => todo.isComplete);
      }
    },
  },
  watch: {
    filter(newFilter) {
      this.filterTodos(newFilter, this.todos);
    },
    todos(todos) {
      this.filterTodos(this.filter, todos);
    },
  },
};
</script>

<template>
  <main>
    <PageHeader />
    <section class="max-w-[600px] mx-auto pt-20">
      <TodoHeader />
      <div class="mt-[20px] shadow-lg bg-transparent">
        <TodoInput @create-todo="addTodo" />
        <TodoItem
          v-for="todo in filteredTodos"
          :key="todo.id"
          :todo="todo"
          @toggle-todo="toggleTodo"
          @remove-todo="removeTodo"
        />
      </div>
      <TodoFilter
        :count="filteredTodos.length"
        :filter="filter"
        @clear-todos="clearCompleted"
        @filter-todos="(newFilter) => (filter = newFilter)"
      />
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
