<script>
  // animation effects for the task items
	import { fly } from 'svelte/transition';
  
  // the main data structure object that holds the list and its owner.
	let todoList = {
		name: "",
		tasks: []
	}
  
  // adds a task into the array inside the main object using spread syntax.
	const addTask = () => {
		todoList.tasks = [...todoList.tasks, ""]
	}
  
  // removes a task from the array inside the main object using [array].slice.
	const removeTask = (index) => {
		todoList.tasks = [...todoList.tasks.slice(0, index), ...todoList.tasks.slice(index+1)]
	}
  
  // saves the current todoList object to the user's laptop.
	const saveTasks = () => {
		localStorage.setItem(todoList.name, JSON.stringify(todoList))
	}
  
  // loads the named todoList object from the user's laptop (if it exists).
	const loadTasks = () => {
		if (localStorage.getItem(todoList.name)) {
			todoList = JSON.parse(localStorage.getItem(todoList.name))
    }
	}
</script>

<style>
	.task, label {
		display: block;
	}
</style>

<!-- sinput for labelling a list to save or finding a saved list. -->
<label>
	Name:
	<input bind:value={todoList.name}>
</label>

<!-- control buttons for the list. -->
<button on:click={addTask}>Add Task 📝</button>

<button on:click={saveTasks}>Save 💾</button>

<button on:click={loadTasks}>Load 📡</button>

<!-- iterates through each item in the tasks array and outputs it as an input with button to remove. -->
{#each todoList.tasks as task, index}
	<div class="task"
			 in:fly="{{ x: 200, duration: 200 }}"
			 out:fly="{{ x: -200, duration: 200 }}">
		<input bind:value={todoList.tasks[index]}>
  	<button on:click={() => { removeTask(index) }}>🗑</button>
	</div>	
{/each}
