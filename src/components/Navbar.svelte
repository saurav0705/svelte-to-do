<script>
import {Link} from "svelte-routing";
import { navigate } from "svelte-routing";

const goToRoute = (url) => navigate(url);
let extended = false;
let toggleNavbar = () => extended = !extended
</script>


<div class={!extended ? "navbar compress":"navbar"} on:click={() => toggleNavbar()}>
<div class="item alternate" >🍔 Svelte 🍔🍕</div>
<div class="item" on:click={() => goToRoute('/')}>🍕Home</div>
<div class="item" on:click={() => goToRoute('/count')}>🍕Count</div>
<div class="item" on:click={() => goToRoute('/todo')}>🍕TODO</div>
<div class="item" on:click={() => goToRoute('/opacity')}>🍕Opacity</div>
</div>

<style type="text/scss">
    .compress{
                height: 60px;
            }
    .navbar{
        display: flex;
        background-color: lightcoral;
        margin: 0;
        padding: 0;
        transition-duration: 300ms;
        
        .alternate{
            display: none;
            text-transform: uppercase;
        }
        .item{
        text-align: left;
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

    @media screen and (max-width:600px){
        .navbar{
            display: block;
            overflow: hidden;
            .alternate{
                display: block;
            }
            .item{
                &:hover{
                    background-color: lightcoral;
                    color: white;
                }
            }
        }
    }
    
</style>