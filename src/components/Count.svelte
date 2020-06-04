<script>
let count  = 0;
let double = 0;
const increment = () => count++;
const decrement = () => count--;
$:  double = count*2;
</script>

<div>
<h1> count :: {count}</h1>
<h1> twice :: {double}</h1>
<button on:click={increment}>⏫</button>
<button on:click={decrement}>⏬</button>
</div>

<style>
button{
    background-color: transparent;
    border: none
}
</style>
