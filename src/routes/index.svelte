<script lang="ts">
	const scale = 5;

	let pailings = 2;
	let pailingWidth = 70;
	let fenceWidth = 3098;
	const pailingHeight = 1200;

	$: gap = (fenceWidth - pailingWidth) / (pailings - 1) - pailingWidth;
</script>

<h1>Fence Calculator</h1>

<label
	>Number of pailings
	<input type="number" bind:value={pailings} />
</label>
<label
	>Pailing Width
	<input type="number" bind:value={pailingWidth} />
</label>
<label
	>Fence Width
	<input type="number" bind:value={fenceWidth} />
</label>

{gap}

<div
	class="fence"
	style:width={`${fenceWidth / scale}px`}
	style:height={`${pailingHeight / scale}px`}
>
	{#each Array.from({ length: pailings }, (_, i) => i) as pailingNo}
		<div
			class="pailing"
			style:width={`${pailingWidth / scale}px`}
			style:height={`${pailingHeight / scale}px`}
			style:margin-right={`${pailingNo < pailings - 1 ? gap / scale : 0}px`}
		>
			&nbsp;
		</div>
	{/each}
</div>

<style>
	.fence {
		display: flex;
		outline: solid 1px black;
	}

	.fence .pailing {
		outline: solid 1px blue;
		background: blue;
	}
</style>
