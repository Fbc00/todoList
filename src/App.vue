<template>
	<div id="app">
		<h1>Tarefas</h1>
		<ProgressTask :progress="percentualFeitos"/>
		<NovaTarefa @addTask="addTaskMain"/>
		<Tarefas @taskDeleted="deletaTask" 
				@taskStateChanged="toggle"
				:tarefas="tasks" />

	</div>
	
</template>

<script>
import ProgressTask from './components/taskPrgress.vue'
import NovaTarefaVue from './components/novaTarefa.vue';
import Tarefas from './components/TarefasAll.vue'
import NovaTarefa from './components/novaTarefa.vue';
export default {
	components: { Tarefas, NovaTarefaVue, NovaTarefa, ProgressTask },
	data() {
		return {
			tasks: [], 
	
		}
	},

	methods: {
		addTaskMain(task) {
			const sameName = t => t.name === task.name
			const novaTask = this.tasks.filter(sameName).length == 0
			if(novaTask) {
				this.tasks.push({name: task.name, pendding:task.pendding})
			}
		},

		deletaTask(i) {
			this.tasks.splice(i, 1)
		}, 
		toggle(i) {
			this.tasks[i].pendding = !this.tasks[i].pendding
		}
	},
	watch: {
		tasks: {
			deep: true,
			handler() {
							 	localStorage.setItem('tasks', JSON.stringify(this.tasks))
			}
		}
	},
	computed: {
		percentualFeitos() {
			const feitos = this.tasks.filter(t => { return !t.pendding})
			const percentual = (feitos.length * 100) / this.tasks.length
			return Math.round(percentual) || 0
		},
	created() {
		const json = localStorage.getItem('tasks')
		json.length ? this.tasks = JSON.parse(json) : this.tasks = []
	}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
