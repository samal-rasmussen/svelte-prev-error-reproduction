<script lang="ts">
	import { onMount } from "svelte";

	interface Item {
		value: string;
		id: number;
	}

	let items = $state<Item[]>([
		{ value: "a", id: 1 },
		{ value: "b", id: 2 },
		{ value: "c", id: 3 },
	]);

	// Error also happens if you use setTimeout instead of onMount
	onMount(() => {
		items = [
			{ value: "a", id: 1 },
			{ value: "b", id: 2 },
			{ value: "b", id: 2 },
			{ value: "c", id: 3 },
		];
	});
</script>

<h1>Child</h1>

<a href="/">Goto root</a>

{#each items as item (item.id)}
	<div>{item.value}</div>
{/each}
