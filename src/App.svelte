<script>
	import SVGTile from "./SVGTile.svelte";
	export let name;
	export let tiles = [{ x: 50, y: 50, s: 100, r: 20, id: 0 }];
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>
		Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
		how to build Svelte apps. OK!
	</p>
	<svg id="tiles" viewBox="0 0 1000 1000">
		{#each tiles as tileInfo (tileInfo.id)}
			<SVGTile {tileInfo} />
		{/each}
	</svg>
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

	svg#tiles {
		width: 50%;
		height: 50%;
	}
</style>
