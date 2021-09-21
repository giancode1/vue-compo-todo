<template>
    <ul class="list-group">
        <todo-item 
            v-for="todo in todos" 
            :key="todo.id" 
            :todo="todo" 
        />

        <TodoFooter
            v-if="todos.length!==0" 
        />
        <li v-else class="list-group-item">Ho hay todos</li>

    </ul>
</template>

<script>
import { inject } from '@vue/runtime-core'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'

export default {

  components: { TodoItem, TodoFooter },

    setup(){
        const todos = inject('todos')

        return{
            todos
        }
    }
}
</script>

<style>

</style>