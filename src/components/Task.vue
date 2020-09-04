<template>
    <div class="column is-5 is-narrow">
        <div @click="$emit('task-state-changed', task)" :class="stateClass">
             <button @click.stop="$emit('task-delete', task)" class="delete"></button>
             <p>{{task.name}}</p>     
        </div>
    </div>               
</template>

<script>
export default {
    props:{
        task: {Type: Object, Required: true}
    },
    computed:{
        stateClass(){
            return{
              "notification is-danger clicavel" : this.task.pending,
              "notification is-success line-through clicavel" : !this.task.pending
            }
        }
    }

}
</script>

<style>
.line-through{
    /* Colocar linha atravessado no texto */
    text-decoration: line-through;
}
.clicavel{
    /* Tornar notificação clicavel */
    cursor: pointer;
    /* Nao deixar que o usuario selecione o texto */
    user-select: none; 
    box-shadow: 3rem;
    box-shadow: 2px 2px 15px  rgb(70, 65, 65);
}

</style>