<script lang="ts">
    let tasks: string[] = [];

    function handleNewTask() {
        tasks = [...tasks, "New Task"];
    }

    function handleDeleteTask(index: number) {
        tasks = [...tasks.slice(0, index), ...tasks.slice(index + 1)]
    }

    function handleTaskChange(index: number, value: string) {
        tasks = [...tasks.slice(0, index), value, ...tasks.slice(index + 1)]
    }
    
</script>

<h1>Simple Todo App</h1>
<button on:click={handleNewTask}>New Task</button>
<ul>
    {#each tasks as task, index}
        <li>
            <input bind:value={task} on:change={() => handleTaskChange(index, task)}>
            <button on:click={() => handleDeleteTask(index)}>Delete</button>
        </li>
    {/each}
</ul>