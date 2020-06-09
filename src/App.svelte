
<script>
	import { Router, Link, Route } from "svelte-routing";
	import AddTask from './components/AddTask.svelte';
	import Count from './components/Count.svelte';
	export let url = "";
</script>

<main>
<Router url="{url}">
	<Route path="/" component="{AddTask}" />
    <Route path="/count" component="{Count}" />
</Router>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
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