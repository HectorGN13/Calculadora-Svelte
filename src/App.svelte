<script>
	import Screen from "./Screen.svelte";
	import Button from "./Button.svelte";
	const teclas = [
		["7", "8", "9","%", "C", "CA"],
		["4", "5", "6", "*", "/", "√"],
		["1", "2", "3", "+", "-", "x²"],
		["±", "0", ".", "="],
	];
	let result = "";
</script>

<main>
	<Screen {result} />
	<div class="teclas">
		{#each teclas as fila}
			<div class="fila">
				{#each fila as tecla}
					<Button {tecla} bind:result />
				{/each}
			</div>
		{/each}
	</div>
</main>

<style>
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	main {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		border-radius: 1em;
		padding: 2em;
		width: 350px;
		background: #616161;
	}
	.fila {
		display: flex;
	}
</style>