<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todosList">
      <TodoItem v-bind:todo="todo"/>
    </div>
  </div>
</template>

<script>
import TodoItem from './Item'
export default {
  name: "TodosItem",
  props: ["todosList"],
  components: {TodoItem}
};
</script>

<style></style>
