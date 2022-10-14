<template>
    <div id="add-container">
        <form @submit="addTodo">
            <input type="text" v-model="title">
        </form>
    </div>
</template>

<script>
import { uuid } from "vue-uuid";
export default {
/* eslint-disable */
    name: 'Add',
    data(){
        return{
            title: ''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();

            const nuevo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            };

            this.title = '';
            this.$emit('add-todo', nuevo);
        }
    }
}
</script>

<style scoped>
#add-container{
    padding: 10px;
}
input{
    padding: 10px;
    outline: none;
    border: solid 1px #ccc;
    width: 100%;
    caret-color: blue;
}
input:focus{
    background-color: #ccc;
    color: #000;
}
</style>