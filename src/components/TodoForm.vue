<template>
  <form @submit.prevent="handleSubmit">
    <input 
        type="text" 
        class="form-control my-3"
        placeholder="Ingrese tarea"
        v-model.trim="input"
    />
  </form>
</template>

<script>
import { inject, ref } from '@vue/runtime-core';
export default {

    setup(){ 
        const todos = inject('todos')
        const input = ref('')

        const handleSubmit = () => {
            if(input.value===''){
                return
            }
            const todo = { 
                id: Date.now(),
                task: input.value,
                completed: false
            }
            todos.value.push(todo)
            input.value = ""
        }

        return{
            handleSubmit,
            input
        }
    }
};
</script>

<style></style>
