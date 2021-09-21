<template>
    <ul class="list-group">
        <TodoFiltro />
        
        <TodoItem 
            v-for="todo in todosShow" 
            :key="todo.id" 
            :todo="todo" 
        />

        <TodoFooter
            v-if="todos.length!==0" 
        />
        <li v-else class="list-group-item">No hay tareas</li>


    </ul>
</template>

<script>
import { computed, inject, provide, ref } from '@vue/runtime-core'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltro from './TodoFiltro.vue'

export default {

  components: { TodoItem, TodoFooter, TodoFiltro },

    setup(){
        const todos = inject('todos')   

        const selection = ref('all')

        const todosShow = computed(()=>{
            if(selection.value === 'all'){
                return todos.value
            }  
            if(selection.value === 'active'){
                return todos.value.filter(item=>item.completed===false)
            }  
            if(selection.value === 'complete'){
                return todos.value.filter(item=>item.completed===true)
            }  
        })

        provide('selection', selection)

        return{
            todos,
            todosShow
        }
    }
}
</script>

<style>

</style>