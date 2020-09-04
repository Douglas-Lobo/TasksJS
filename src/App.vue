<template>
   <section class="hero is-fullheight">
  <div class="hero-body has-text-centered">
    <div class="container">
        <NewTask
          @add-task='newTask'
        />
          <TaskGrid v-if="tasks.length"
          @task-state-changed="toggleTaskState" 
          @task-delete='taskDelete'
          :tasks='tasks' 
           />
           <p v-else>Adicione uma tarefa!!</p>
    </div>
  </div>
</section>

 
</template>

<script>
import TaskGrid from "./components/TaskGrid.vue";
import NewTask from "./components/NewTask.vue";

export default {
  components:{ TaskGrid, NewTask },
  data(){
    return{
      tasks: []
    }
  },
  methods:{
    toggleTaskState(i){
        this.tasks[i].pending = !this.tasks[i].pending
    },
    taskDelete(i){
        this.tasks.splice(i,1)
    },
    newTask(task){
          const sameName = t =>t.name === task.name
          const reallyNew = this.tasks.filter(sameName).length == 0
          if (reallyNew) {
              this.tasks.push({
                name: task.name,
                pending: task.pending || true
              })
          }
    }
  }

}
</script>

<style scoped>
  
  h1{
    font-size: 3rem;
  }

</style>