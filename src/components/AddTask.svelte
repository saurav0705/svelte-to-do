<script>
import { fade,fly } from 'svelte/transition';
let task = "";
let taskList = [];
const addTask = () => {
    taskList = [...taskList,{task:task,done:false}];
    task=""
}
const removeTask = (ind) => {
    taskList = [...taskList.filter((task,index) => index!==ind )]
    
}
const toggleDone = (index) => {
    let obj = taskList;
    obj[index].done = !obj[index].done;
    taskList = [...obj];
    console.log(taskList);
}
</script>

<div class="input">
<input bind:value={task}/><button on:click={addTask}>🏓</button>
{#if taskList.length === 0 }
<div class="no-task" transition:fade>Add some task you lazy dummy</div>
{/if}

{#each taskList as item,index}
    <div class="task" in:fly="{{ y: 200, duration: 2000 }}" out:fade>
    <div class={item.done ? "task-item strike":"task-item"}>{item.task}</div>
    <div class="delete"><span on:click={() => toggleDone(index)}>🆗</span><span  on:click={() => removeTask(index)}>❎</span></div>
    </div>
{/each}
</div>

<style>
.no-task{
    text-align: center;
    font-size: 34px;
    font-weight: 500;
    text-transform: capitalize;
}
.task{
    display: flex;
    justify-content: space-between;
    max-width: 600px;
    width: auto;
    margin: auto;
    background-color: lightblue;
    margin-top: 2px;
    padding: 10px; 
}
.delete{
    cursor: pointer;
}
.strike{
    text-decoration: line-through;
}

</style>