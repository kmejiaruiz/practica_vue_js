<template>
  <div class="todo" v-bind:class="{ completed: todo.completed }">
    <div class="body">
      <input
        type="checkbox"
        v-bind:checked="todo.completed ? 'checked': ''"
        v-on:change="checkTodo"
      >
      {{ todo.title }}
    </div>

    <div class="acciones">
      <button @click="$emit('borrar', todo.id)">Eliminar</button>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    checkTodo() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo {
  border-bottom: 1px solid #ccc;
  padding: 10px;
}
.todo:not(.completed):hover {
  background-color: #ddd9d9;
}
.completed {
  color: #eee;
  text-decoration: line-through;
}
.completed .body {
  text-decoration: line-through;
}
.body,
.acciones {
  display: inline-block;
  vertical-align: top;
}
.body {
  width: 85%;
}
.acciones {
  padding: 0 10px;
  width: 10%;
}
button {
  border: none;
  border-radius: 3px;
  padding: 10px;
  background-color: #c2c1c1;
  color: #000;
}
button:hover {
  background-color: #da2020;
  color: #fff;
}
@media screen and (max-width:798px) {
  .acciones{
    padding: 0 !important;
  }
  button{
    /* padding: 5px !important; */
    margin-left: -15px;
  }
}
/* @media screen and (max-width:422px) {
  button{
    margin-left: -25px !important;
  }
} */
</style>