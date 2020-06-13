<script>
import { fade,fly } from 'svelte/transition';
export let list;
export let heading;
export let removeTask;
export let toggleDone;
</script>

<div class="list-component">
{#if list.length!==0}
<div class="heading">{heading}</div>
{#each list as item,index}
    <div class={item.done ? "task done":"task"} in:fly="{{ y: 200, duration: 2000 }}" out:fade|local>
    <div class={item.done ? "task-item strike":"task-item"}>{item.task}</div>
    <div class="delete"><span class="done-btn" on:click={() => toggleDone(index)}>{item.done ? "undone":"done"}</span><span  on:click={() => removeTask(index)}>❎</span></div>
    </div>
{/each}
{/if}
</div>


<style>
.list-component{
    flex:1;
    margin: 2vh;
}
.done-btn{
    text-transform: uppercase;
    background-color: #2d2d2d;
    color: white;
    padding: 2px;
    border-radius: 5px;
}
.heading{
    font-size: 32px;
    font-weight: 700;
    text-transform: uppercase;
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
    font-size: 20px;
}

.delete{
    cursor: pointer;
}
.strike{
    text-decoration: line-through;
    color: white;
}
.done{
    background-color: lightcoral;
}

</style>