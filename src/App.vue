<template>
  <div>
    <div id="header"></div>
    <div id="main-container">
      <h2>Todos</h2>
      <Todos v-bind:todosList="copyTodos"/>
    </div>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
// import search from "./components/Search.vue";
import Todos from "./components/Todos";
// import todoApp from "./components/TodoAdd.vue";

export default {
  name: "App",
  components: {
    Todos
  },
  data() {
    return {
      TodosItem: [
        {
          id: 0,
          title: "comprar cerveza",
          completed: false,
        },
        {
          id: 1,
          title: "pasear al perro",
          completed: true,
        },
        {
          id: 2,
          title: "jugar a la xbox",
          completed: false,
        },
        {
          id: 3,
          title: "Instalar Windows",
          completed: true,
        },
      ],
      copyTodos: [],
    };
  },
  created() {
    this.copyTodos = [...this.TodosItem];
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.5rem;
  padding: 0;
  margin: 0;
}
#main-container {
  border: solid 1px #ccc;
  width: 600px;
  margin: 100px auto;
}
</style>
