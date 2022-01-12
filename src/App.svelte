<script>
	import SVGTile from "./SVGTile.svelte";
	export let name;
	export let tiles = [
		{ x: 50, y: 50, s: 100, r: 20, id: 0, selected: false },
	];
	function addTile() {
		tiles.push({
			x: 0,
			y: 0,
			s: 100,
			r: 20,
			id: tiles.length,
			selected: false,
		});
		tiles = tiles;
	}
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>
		Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
		how to build Svelte apps. OK!
	</p>
	<button on:click={addTile}>New Tile</button>
	<svg id="tiles">
		{#each tiles as tileInfo (tileInfo.id)}
			<SVGTile bind:tileInfo />
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
		width: 600px;
		height: 300px;
	}
</style>
