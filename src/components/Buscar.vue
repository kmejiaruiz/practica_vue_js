<template>
    <div id="buscar-container">
        <input type="text" v-model="query" v-on:input="$emit('query-change', query)">
    </div>
</template>

<script>
/* eslint-disable */
export default {
    name: 'Buscar',
    data(){
        return{
            query: ''
        }
    }
}
</script>
<style scoped>
#buscar-container{
    width: 600px;
    margin: 0 auto;
}
input{
    padding: 10px;
    width: 100%;
    outline: none;
}
@media screen and (max-width:798px) {
    input{
        width: 100%;
    }
    #buscar-container{
        width: auto !important;
        margin-left: 10%;
        margin-right: 10%;
    }
}
</style>