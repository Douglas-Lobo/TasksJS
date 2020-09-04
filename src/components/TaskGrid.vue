<template>
<div class="columns is-multiline is-mobile is-centered">
    <Task v-for="(task, i) in tasks" :key="task.id" 
        :task='task' 
        @task-state-changed="$emit('task-state-changed', i)"
        @task-delete="$emit('task-delete', i)"
    />
</div>
  
</template>

<script>
import Task from "./Task";
export default {
    components:{ Task },
    props:{
        tasks: {Type: Array, Required: true}
    }
}
</script>

<style>

</style>