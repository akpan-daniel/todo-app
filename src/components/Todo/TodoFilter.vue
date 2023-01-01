<script>
export default {
  emits: ["clear-todos", "filter-todos"],
  props: {
    count: Number,
    filter: Boolean,
  },
  methods: {
    clearTodos() {
      this.$emit("clear-todos");
    },
    filterTodos(filter) {
      this.$emit("filter-todos", filter);
    },
  },
};
</script>

<template>
  <section
    class="h-[50px] bg-gray-200 dark:bg-gray-800 rounded-b-lg p-4 text-sm border-gray-500"
    :class="count === 0 ? 'rounded-t-lg' : 'border-t-[1px]'"
  >
    <div class="flex justify-around items-center text-gray-500 font-thin">
      <p>{{ count }} item (s) left</p>
      <div class="flex gap-3 text-center">
        <span
          :class="filter === null && 'active'"
          @click="() => filterTodos(null)"
          >All</span
        >
        <span
          :class="filter === true && 'active'"
          @click="() => filterTodos(true)"
          >Active</span
        >
        <span
          :class="filter === false && 'active'"
          @click="() => filterTodos(false)"
          >Completed</span
        >
      </div>
      <p class="clear-complete" @click="clearTodos">Clear Completed</p>
    </div>
  </section>
</template>

<style scoped>
span,
.clear-complete {
  transition: all 0.2s ease-in;
}

span:hover,
.clear-complete:hover {
  cursor: pointer;
  color: #eee;
}

.active {
  color: hsl(220, 98%, 61%);
}
</style>
