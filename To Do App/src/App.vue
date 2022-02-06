<template>
  <Header />
  <main>
    <h1>My Tasks</h1>
    <div class="main_content">
      <Screens :data="$data" @back="back" />
    </div>
    <div class="buttons">
      <Buttons
        :data="$data"
        :buttonTypes="buttonTypes"
        @add="add"
        @create="create"
        @deleted="deleted"
        @back="back"
      />
    </div>
  </main>
</template>

<script>
import Header from "./components/Header.vue";
import Screens from "./components/Screens.vue";
import Buttons from "./components/Buttons.vue";
export default {
  name: "App",
  components: {
    Header,
    Screens,
    Buttons,
  },
  data() {
    return {
      todos: [],
      newTodo: "",
      newDescription: "",
      nextTodoId: 0,
      descriptionId: null,
      buttonTypes: {
        add: true,
        create: false,
        deleted: false,
      },
      showScreens: {
        todoList: true,
        addNewTodo: false,
        description: false,
      },
    };
  },
  methods: {
    time() {
      return Date().split(" ").splice(0, 5).join(" ");
    },
    add() {
      this.showScreens.todoList = false;
      this.showScreens.addNewTodo = true;
    },
    create() {
      if (this.newTodo.replaceAll(" ", "").length) {
        this.todos.push({
          id: this.nextTodoId++,
          title: this.newTodo,
          description: this.newDescription,
          isDone: false,
          created: this.time(),
        });
        this.newTodo = "";
        this.newDescription = "";

        this.showScreens.addNewTodo = false;
        this.showScreens.todoList = true;
      }
    },
    back() {
      this.showScreens.todoList = true;
      this.showScreens.addNewTodo = false;
      this.showScreens.description = false;

      this.buttonTypes.add = true;
      this.buttonTypes.create = false;
      this.buttonTypes.deleted = false;

      this.newTodo = "";
      this.newDescription = "";
    },
    deleted(id) {
      this.todos.splice(this.descriptionId, 1);
      this.back();
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background: #2c3e50;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  color: #fff;
  /* margin-top: 60px; */
}

.main_content {
  margin: 0 auto;
  border: 1px solid #202020;
  border-radius: 20px;
  max-width: 700px;
  width: 90%;
  min-width: 300px;
  background: #3b3b3b;
  padding: 10px 0;
}

.buttons {
  margin: 0 auto;
  max-width: 700px;
  width: 90%;
  min-width: 300px;
}
h1 {
  margin: 40px 0 10px;
}
</style>
