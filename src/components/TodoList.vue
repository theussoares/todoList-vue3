<template>
    <div style="background-color: #f046;"
        class="container">
        <Todo />
    </div>
</template>

<script>
import Todo from './Todo.vue'

export default {
  name: 'TodoList',
  components: {
    Todo
  }
}
</script>

<style scoped>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding-bottom: 10px;
        gap: 10px;
    }
</style>