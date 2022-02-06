<template>
  <div class="desc_header">
    <h1>
      {{ todo.title }}
    </h1>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke="currentColor"
      @click="back"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z"
      />
    </svg>
  </div>

  <div class="description">
    <template v-if="todo.description">
      {{ todo.description }}
    </template>
    <template v-else> Without Description </template>
  </div>
  <div class="times"></div>
  <p id="create">created: {{ todo.created }}</p>
</template>

<script>
export default {
  props: ["todo"],
  methods: {
    back() {
      this.$emit("back");
    },
  },
};
</script>

<style scoped>
.desc_header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  margin: 5px 0 0 20px;
  text-align: left;
  font-family: Stencil;
  font-size: 30px;
}

svg {
  width: 30px;
  height: 30px;
  cursor: pointer;
  margin: 0 15px 0 0;
}

path {
  color: #202020;
}

.description {
  text-align: left;
  margin: 30px 0 30px 20px;
  width: 70%;
  text-align: justify;
  color: #808080;
}

p {
  margin: 0 10px 5px 20px;
  text-align: left;
  color: rgb(255, 49, 49);
}
</style>