<script>
import {Link} from "svelte-routing";
import { navigate } from "svelte-routing";

const goToRoute = (url) => navigate(url);
</script>


<div class="navbar">
<div class="item" on:click={() => goToRoute('/')}>Home</div>
<div class="item" on:click={() => goToRoute('/count')}>Count</div>
<div class="item" on:click={() => goToRoute('/todo')}>TODO</div>
<div class="item" on:click={() => goToRoute('/opacity')}>Opacity</div>
</div>

<style type="text/scss">
    .navbar{
        display: flex;
        // justify-content: space-between;
        background-color: lightcoral;
        margin: 0;
        padding: 0;
        .item{
        padding: 2vh;
        font-weight: 500;
        text-transform: uppercase;
        font-size:24px;
        color:white;
        cursor: pointer;
        transition-duration: 200ms;
        // border-bottom: 2px solid lightcoral;
        &:hover{
            background-color: white;
            color: lightcoral;
        }
        }
    }
    
</style>