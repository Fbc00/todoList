<template>
  <div class="newTask">
    <input type="text" v-model="name" @keydown.enter="add" 
    class="form-element" placeholder="Nova tarefa?">
    <button class="form-element"  @click="add">+</button>
  </div>
</template>

<script>
export default {
    data () {
        return {
            name: ''
        }
    },

    methods: {
        add() {
            this.$emit('addTask', {name: this.name, pendding: false})
            this.name = ''
        }
    }

}
</script>

<style scoped>
    .newTask {
        margin: 35px;

    }
    .form-element {
        outline: none;
        font-size: 2rem;
        border: 1px solid #fff;
        padding: 5px 10px 8px;
        color: #fff;
    }
    input.form-element {
        width: 500px;
        background: #fff2;
        border-top-left-radius: 8px;
        border-bottom-left-radius: 8px;
    }

    button.form-element {
        border-left: none;
        background-color: #2196f3;
        border-top-right-radius: 8px;
        border-bottom-right-radius: 8px;
        cursor: pointer;
    }
</style>