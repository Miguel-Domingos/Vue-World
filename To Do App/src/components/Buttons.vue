<template>
  <button v-if="buttonTypes.add" @click="add">Add new</button>
  <button v-if="buttonTypes.create" @click="create">Create</button>
  <button v-if="buttonTypes.back" @click="back">Back</button>
  <button v-if="buttonTypes.deleted" @click="deleted">deleted</button>
</template>

<script>
export default {
  props: ["data", "buttonTypes"],
  methods: {
    add() {
      this.$emit("add");

      this.buttonTypes.add = false;
      this.buttonTypes.create = true;
      this.buttonTypes.back = true;
      this.buttonTypes.deleted = false;
    },
    create() {
      if (this.$props.data.newTodo.replaceAll(" ", "").length) {
        this.$emit("create");
        this.buttonTypes.add = true;
        this.buttonTypes.create = false;
        this.buttonTypes.deleted = false;
        this.buttonTypes.back = false;
      }
    },
    back() {
      this.$emit("back");
      this.buttonTypes.add = true;
      this.buttonTypes.back = false;
    },
    deleted() {
      this.$emit("deleted");
    },
  },
};
</script>

<style scoped>
button {
  color: #ff0000;
  background: transparent;
  border: 1px solid #ff0000;
  border-radius: 5px;
  padding: 8px 11px;
  margin-top: 20px;
  float: right;
  cursor: pointer;
  margin-left: 10px;
}
</style>