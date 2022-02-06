<template>
  <ul v-if="todos.length > 0">
    <Todo
      v-for="(todo, index) in todos"
      :key="todo.id"
      :title="todo.title"
      :index="index"
      :class="[todo.isDone ? 'isDone' : '']"
      @description="description"
      @deleted="deleted"
      @isDone="isDone"
    />
  </ul>
  <span class="SemTarefas" v-else>No 'ToDo' at the moment</span>
</template>

<script>
import Todo from "./Todo.vue";

export default {
  props: ["todos"],
  components: {
    Todo,
  },
  methods: {
    description(id) {
      this.$emit("description", id);
    },
    deleted(id) {
      this.$emit("deleted", id);
    },
    isDone(id) {
      this.$props.todos[id].isDone = !this.$props.todos[id].isDone;
    },
  },
};
</script>

<style scoped>
ul {
  padding: 0;
  width: 100%;
}

.SemTarefas {
  color: red;
  font-size: 1.2em;
}
</style>