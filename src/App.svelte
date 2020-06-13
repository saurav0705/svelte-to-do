
<script>
	import { Router, Link, Route } from "svelte-routing";
	import AddTask from './components/AddTask.svelte';
	import Count from './components/Count.svelte';
	import Navbar from './components/Navbar.svelte';
	import Opacity from './components/Opacity.svelte';
	export let url = "";
</script>

<main>
<Router url="{url}">
	<Navbar/>
	<Route path="/todo" component="{AddTask}" />
    <Route path="/count" component="{Count}" />
	<Route path="/opacity" component="{Opacity}" />
</Router>
</main>

<style>

	main {
		text-align: center;
		
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>