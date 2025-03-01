<template>
    <h1>Lista de tarefas </h1>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            {{ todo.title }}
        </li>
    </ul>
</template>

<script>
import { onMounted, ref } from 'vue';
import TodoService from '@/services/todos.service';

export default {
    name: 'TodosIndex',
    setup() {
        const todos = ref([])
       onMounted(() => {
        TodoService.getAll().then(response => { todos.value = response.data.data})
        .catch(error => console.log(error))
       })

       return {
            todos,
       }

    }
}

</script>