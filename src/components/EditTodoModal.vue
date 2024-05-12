<template>
    <div class="modal">
      <div class="modalContent">
        <h2>Editar Tarefa</h2>
        <input v-model="editedTodo" placeholder="Editar tarefa" />
        <button @click="saveEdit">Salvar</button>
        <button @click="cancelEdit">Cancelar</button>
      </div>
    </div>
</template>
  
<script>
  export default {
    props: ['todoText'],
    data() {
      return {
        editedTodo: ''
      };
    },
    mounted() {
      this.editedTodo = this.todoText;
    },
    methods: {
      saveEdit() {
        this.$emit('save', this.editedTodo);
      },
      cancelEdit() {
        this.$emit('cancel');
      }
    }
  };
</script>
  
  <style scoped>
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7); /* Fundo semi-transparente para o modal */
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  
  .modal-content {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
  }
  h2{
    color: #fff;
}
  input {
    width: 100%;
    margin-bottom: 10px;
  }
  button{
    margin-left: 5px;
    margin-right: 5px;
    border-radius: 5px;
    border: none;
    background-color: #f046;
    color: #fff;
    padding: 5px;
  }
</style>
  