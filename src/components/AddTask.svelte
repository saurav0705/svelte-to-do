<script>
import { fade,fly } from 'svelte/transition';
import List from './List.svelte';
let task;
let taskList = [];
let taskDone = [];
const addTask = () => {
    taskList = [...taskList,{task:task,done:false}];
    task=""
}
const removeTaskList = (ind) =>   taskList = [...taskList.filter((task,index) => index!==ind )]

const removeTaskDone = (ind) =>   taskDone = [...taskDone.filter((task,index) => index!==ind )]

const toggleDoneTrue = (index) => {
    let obj = [...taskList];
    obj[index].done = !obj[index].done;
    taskDone = [...taskDone,obj[index]];
    removeTaskList(index);
}
const toggleDoneFalse = (index) => {
    let obj = [...taskDone];
    obj[index].done = !obj[index].done;
    taskList = [...taskList,obj[index]];
    removeTaskDone(index);
}

</script>
<div class="heading">Made with svelte with 💓</div>
<div class="input">
<input bind:value={task}/><button on:click={addTask}>🏓</button>
{#if taskList.length===0 && taskDone.length===0}
<div class="no-task" transition:fade>Add some task you lazy dummy</div>
{/if}
<div class="task-view">
<List heading="Todo" list={taskList} removeTask={removeTaskList} toggleDone={toggleDoneTrue}/>
<List heading="DONE" list={taskDone} removeTask={removeTaskDone} toggleDone={toggleDoneFalse}/>
</div>
</div>

<style>
.task-view{
    display: flex;
    justify-content: center;
}
.heading{
    font-size: 42px;
    text-transform: uppercase;
    text-align: center;
    padding: 10px;
    margin-bottom: 10vh;
    color: orange
}
.no-task{
    text-align: center;
    font-size: 30px;
    font-weight: 500;
    text-transform: capitalize;
}


</style>