<script>
export default {
  emits: ["toggle-todo", "remove-todo"],
  props: {
    todo: Object,
  },
  methods: {
    toggle() {
      this.$emit("toggle-todo", this.todo.id);
    },
    remove() {
      this.$emit("remove-todo", this.todo);
    },
  },
};
</script>

<template>
  <div
    class="todo-item flex justify-between h-[65px] bg-gray-200 border-b dark:border-gray-500 transition-all duration-200 hover:scale-[0.98] cursor-pointer shadow hover:shadow-lg dark:bg-gray-800"
  >
    <div class="flex">
      <div class="w-[65px] flex justify-center items-center">
        <input
          class="checkbox h-6 w-6 flex border-1 border-gray-600 justify-center items-center cursor-pointer"
          type="checkbox"
          :id="todo.id"
          :checked="todo.isComplete"
          @click="toggle"
        />
      </div>
      <label
        class="flex justify-center p-4 items-center cursor-pointer transition duration-200"
        :class="
          todo.isComplete
            ? 'text-gray-400 dark:text-gray-500 line-through'
            : 'text-gray-700 dark:text-gray-200'
        "
        :for="todo.id"
        >{{ todo.name }}</label
      >
    </div>
    <div class="flex justify-center items-center w-[65px]">
      <img
        @click="remove"
        class="h-6 w-6"
        src="/assets/images/icon-cross.svg"
        alt="delete"
      />
    </div>
  </div>
</template>

<style>
.todo-item:first-of-type {
  border-top-left-radius: 0.5rem;
  border-top-right-radius: 0.5rem;
}
.todo-item:last-of-type {
  border-bottom-left-radius: 0.5rem;
  border-bottom-right-radius: 0.5rem;
  border-bottom: 0px;
}

.checkbox {
  /* removing default appearance */
  -webkit-appearance: none;
  appearance: none;
  /* creating a custom design */
  border-radius: 50%;
  border-width: 1px;
  /* border: 1px solid; */
}

input.checkbox:checked {
  background: linear-gradient(135deg, #55ddff 0%, #c058f3 100%);
}

.checkbox:checked::before {
  content: url("/assets/images/icon-check.svg");
  color: #fff;
}
</style>
