<script>
	import MindElixir from 'mind-elixir'
	import { onMount } from 'svelte'

	let isLoading = true

	onMount(async () => {
		isLoading = false

		let mind = new MindElixir({
			el: '#map',
			direction: MindElixir.LEFT,
			// or set as data that is return from `.getAllData()`
			// data: {...},
			draggable: true, // default true
			contextMenu: true, // default true
			toolBar: true, // default true
			nodeMenu: true, // default true
			keypress: true, // default true
		})
		mind.init(MindElixir.new('new topic'))

		mind.bus.addListener('operation', (operation) => {
			if (operation !== 'beginEdit') {
				//const data = mind.getAllData()
			}
		})
	})
</script>

{#if isLoading}
	<div id="loading">
		<h1>Loading...</h1>
	</div>
{/if}

<div id="map" />

<style>
	#map {
		height: 100vh;
		width: 100vw;
	}

	#loading {
		display: flex;
		place-items: center;
	}
</style>
