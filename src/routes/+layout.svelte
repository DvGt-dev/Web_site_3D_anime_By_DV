<div class="scene">
	<slot />
</div>

<svelte:head>
	<title>DJONTSO page 3D application</title>
</svelte:head>

<style>
	.scene {
		position: absolute;
		inset: 0;
		background: radial-gradient(hsl(220 14% 20%), hsl(220 20% 10%));
	}
</style>
