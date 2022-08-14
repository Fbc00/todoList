<template>
    <div class="task-all">
        <template v-if="tarefas.length">
            <Task v-for="(task,i) in tarefas" :key="task.name" :taskObject="task"
            @taskStateChanged="$emit('taskStateChanged', i)" 
            @taskDeleted="$emit('taskDeleted', i)"></Task> 

        </template>
        <p class="no-task" v-else> Tudo ok na sua vida</p>
    </div>
  

</template>

<script>
import Task from '@/components/Tarefa'
export default {
    components: {Task},
    props:{ 
        tarefas: {
            type: Array
        }

    },
    data() {
        return {

        }
    }
}
</script>

<style scoped>
    .task-all {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 2rem;
    }
    .no-task {
        color: aliceblue;
        font-size: 1.7rem;
    }

</style>