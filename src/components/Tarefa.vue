<template>
    <div class="task" :class="stateClass"
        @click="$emit('taskStateChanged', taskObject)">
        <span class="close" @click.stop="$emit('taskDeleted', taskObject)">X</span>
        <p> {{ taskObject['name']}}</p>
    </div>
</template>
<script>
export default {
    props: {
        taskObject:{ type: Object, required: true}
    },
    computed: {
        stateClass() {
            return {
                pendding: this.taskObject.pendding,
                done: !this.taskObject.pendding
            }
        }
    }

}
</script>

<style scoped>
    .task {
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 8px;
        font-size: 2rem;
        font-weight: 300;
        cursor: pointer;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 10px;
    }
    .pendding {
        border-left: 12 solid #b73229;
        background-color: red;
    }
    .done {
        color: aliceblue;
        border-left: 12px solid #0A8F08;
        background-color: #4CAF50;
        text-decoration: line-through;
    }
    .pendding .close {
        background-color: #b73229;
    }
    .done .close {
        background-color: #0A8F08;
    }

    .close {
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 1rem;
        font-weight: 600;
        height: 25px;
        width: 25px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        text-align: center;
        align-self: center;
    }
</style>
