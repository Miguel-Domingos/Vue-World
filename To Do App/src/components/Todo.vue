<template>
  <li>
    <div @click="description" class="title">
      {{ title }}
    </div>
    <button>
      <svg
        @click="isDone"
        class="isDoneButton"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
        />
      </svg>
    </button>
    <button>
      <svg
        @click="deleted"
        class="delete"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 20 20"
        fill="currentColor"
      >
        <path
          fill-rule="evenodd"
          d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z"
          clip-rule="evenodd"
        />
      </svg>
    </button>
  </li>
</template>

<script>
export default {
  props: ["title", "index"],
  methods: {
    description() {
      this.$emit("description", this.$props.index);
    },
    deleted() {
      this.$emit("deleted", this.$props.index);
    },
    isDone() {
      this.$emit("isDone", this.$props.index);
    },
  },
};
</script>

<style scoped>
li {
  font-family: Stencil;
  width: 85%;
  list-style: none;
  margin: 0 auto 20px;
  padding: 10px 15px;
  border: 1px solid #101010;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

svg {
  width: 25px;
  height: 25px;
}

.isDoneButton {
  color: #101010;
}

.isDone .isDoneButton path {
  color: #00b7ff;
}
.delete {
  color: #ff0000dd;
}
.title {
  width: 100%;
  text-align: left;
  cursor: pointer;
}

button {
  padding: 0;
  margin: 0;
  background: transparent;
  border: transparent;
  margin: 0 -10px -3px 15px;
  cursor: pointer;
}
</style>