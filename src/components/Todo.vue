<template>
    <AddTodo  @add="addTodoToList"/>
    <div class="todo"
        v-for="(todo, index) in todos"
        :key="index">
        <span class="todoText">{{ todo.text }}</span>
        <div class="buttonContainer">
            <button @click="openEditModal(index)">
                Editar
            </button>
            <button @click="deleteTodo">
                Remover
            </button>
        </div>
        <EditTodoModal 
        v-if="showEditModal" :todoText="editedTodoText"
        @save="saveEdit" @cancel="cancelEdit" />
    </div>
</template>

<script>
import AddTodo from './AddTodo.vue';
import EditTodoModal from './EditTodoModal.vue';

export default {
    components: {
        AddTodo,
        EditTodoModal
    },
    data(){
        return {
            todos: [],
            showEditModal: false,
            editedTodoIndex: null,
            editedTodoText: ''
        }
    },
    methods: {
        addTodoToList(newTodo) {
            this.todos.push({ text: newTodo });
        },
        deleteTodo(index) {
            this.todos.splice(index, 1)
        },
        openEditModal(index) {
            this.showEditModal = true;
            this.editedTodoIndex = index;
            this.editedTodoText = this.todos[index].text;
        },
        saveEdit(editedTodo) {
            this.todos[this.editedTodoIndex].text = editedTodo;
            this.closeEditModal();
        },
        cancelEdit() {
            this.closeEditModal();
        },
        closeEditModal() {
            this.showEditModal = false;
            this.editedTodoIndex = null;
            this.editedTodoText = '';
        }
    }
};
</script>


<style scoped>
    .todo{
        background-color: transparent;
        border: 1px solid black;
        border-radius: 5px;
        width: 310px;
        height: 60px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        flex-wrap: wrap;
        overflow-x: auto;
        overflow-y: auto;
        padding: 5px;
    }
    .todoText {
        display: inline-block;
        vertical-align: middle; 
        max-width: calc(100% - 100px); 
    }
    .buttonContainer{
        display: flex;
        gap: 10px;
    }
    button{
        border-radius: 5px;
        border: none;
        background-color: #333;
        color: #fff;
        padding: 5px;
    }
</style>