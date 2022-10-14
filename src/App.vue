<template>
  <div>
    <div id="header">
      <Buscar v-on:query-change="busqueda"/>
    </div>
    <div id="main-container">
      <h2 class="banner">Tareas pendientes</h2>
      <Add v-on:add-todo="addTodo"/>
      <Todos v-bind:todosList="copyTodos" v-on:borrar='borrar'/>
    </div>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Buscar from "./components/Buscar";
import Todos from "./components/Todos";
import Add from "./components/Add";

export default {
  name: "App",
  components: {
    Todos, Add, Buscar
  },
  methods:{
    borrar(id){
      this.TodosItem = this.TodosItem.filter(todo => todo.id != id);
      this.copyTodos =[... this.TodosItem];
    },
    addTodo(todo){
      this.TodosItem.push(todo);
      this.copyTodos = [... this.TodosItem]
    },
    busqueda(query){
      if (query.trim()=== '') {
        this.copyTodos = [...this.TodosItem];
      } else{
        const temp = this.TodosItem.filter(todo => {
          return todo.title.includes(query)
        });
        this.copyTodos = [...temp]
      }
    },
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
.banner{
  text-align: center;
  font-weight: lighter;
}
#header{
  background: black;
  padding: 10px;
  }
#main-container {
  border: solid 1px #ccc;
  width: 600px;
  margin: 100px auto;
}





@media screen and (max-width:798px) {
  #main-container{
    width: auto;
  }
}

</style>
