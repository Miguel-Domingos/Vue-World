<template>
  <NewTodo v-if="data.showScreens.addNewTodo" :data="data" />
  <Todos
    :todos="data.todos"
    v-if="data.showScreens.todoList"
    @description="description"
    @deleted="deleted"
  />
  <Description
    :todo="data.todos[this.$props.data.descriptionId]"
    v-if="data.showScreens.description"
    @back="back"
  />
</template>

<script>
import Todos from "./Todos.vue";
import Description from "./Description.vue";
import NewTodo from "./NewTodo.vue";
export default {
  props: ["data"],
  components: {
    Todos,
    Description,
    NewTodo,
  },
  methods: {
    description(id) {
      this.$props.data.showScreens.todoList = false;
      this.$props.data.showScreens.description = true;

      this.$props.data.buttonTypes.add = false;
      this.$props.data.buttonTypes.create = false;
      this.$props.data.buttonTypes.deleted = true;

      this.$props.data.descriptionId = id;
    },
    deleted(id) {
      this.$props.data.todos.splice(id, 1);
    },
    back() {
      this.$emit("back");
    },
  },
};
</script>

<style>
</style>