<template>
    <h1>Lista de Afazeres</h1>  
    <div>
        <input 
            v-model="newTodo" 
            placeholder="Adcionar nova tarefa"
        >
        <button @click="addTodo">
            Adicionar
        </button>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                newTodo: "",
            }
        },
        methods: {
        addTodo() {
            if (this.newTodo.trim() !== "") {
                this.$emit("add", this.newTodo); // Emitir evento para adicionar nova tarefa
                this.newTodo = "";
            }
        }
    }
};
</script>

<style scoped>
    h1{
        color: #fff;
    }
    div{
        display: flex;
        gap: 20px;
    }
    input{
        border-radius: 5px;
        border: none;
        background-color: #333;
        color: #fff;
    }
    input::placeholder{
        color: #fff;
        padding: 10px;
    }
    button{
        border-radius: 5px;
        border: none;
        background-color: #333;
        color: #fff;
        padding: 5px
    }
</style>