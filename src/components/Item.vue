<template>
  <div class="todo" v-bind:class="{ completed: todo.completed }">
    <div class="body">
      <input
        type="checkbox"
        v-bind:checked="todo.completed"
        @change="checkTodo, event"
      />
      {{ todo.title }}
    </div>

    <div class="acciones">
      <button>Eliminar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return{
        event: this.todo.completed,
    };
  },
  methods: {
    checkTodo() {
      this.event = !this.event;
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
  background-color: #eee;
  color: #000;
}
button:hover {
  background-color: #da2020;
  color: #fff;
}
</style>