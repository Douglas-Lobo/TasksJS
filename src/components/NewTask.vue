<template>

    <div class="column is-8 is-offset-2 is-mobile">
        <input @keydown.enter="add" class="input" type="text" placeholder="Escreva sua nova tarefa ;)" v-model="name" >
    </div>
 
</template>

<script>
export default {
    data(){
        return{
            name: ""
        }
    },
    methods:{
        add(){
            this.$emit('add-task', {name: this.name})
            this.name = ""
        }
    }
};
</script>

<style>
</style>