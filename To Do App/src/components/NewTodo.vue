<template>
  <div>
    <p>Name</p>
    <input type="text" v-model="data.newTodo" placeholder="Task Name" />
  </div>
  <div>
    <p>Description</p>
    <textarea
      v-model="data.newDescription"
      placeholder="Some Description( Optional )"
      name=""
      id=""
    ></textarea>
  </div>
</template>

<script>
export default {
  props: ["data"],
};
</script>

<style scoped>
div {
  width: 100%;
}
p {
  text-align: left;
  margin: 0 0 10px 20px;
  font-family: consolas;
  font-size: 1.3em;
}

input,
textarea {
  font-family: consolas;
  border: 1px solid #101010;
  background: rgba(255, 255, 255, 0.2);
  font-size: 1em;
  color: white;

  width: 90%;
  list-style: none;
  margin: 0 auto 20px;
  padding: 10px 15px;
  border-radius: 10px;
}

textarea {
  resize: none;
  min-height: 150px;
}
</style>