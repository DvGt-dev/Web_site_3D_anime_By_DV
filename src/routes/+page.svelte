


<script>
	import App from '$lib/components/App.svelte'
</script>
  

<div class="container">
	<App />
	<h1>DJONTSO</h1>
	<h1>Examples</h1>

	<ul>
		<li>
			<a href="/sphere">Sphere</a>
		</li>
		<li>
			<a href="/models">Models</a>
		</li>

	</ul>
</div>


<style>
		:global(body) {
	  margin: 0;
	}
  
	div {
	  width: 100vw;
	  height: 10vh;
	  background: rgb(13, 19, 32);
	  background: linear-gradient(180deg, rgba(13, 19, 32, 1) 0%, rgba(8, 12, 21, 1) 100%);
	}

	:global(body) {
		font-family: sans-serif;
		color: hsl(0, 11%, 85%);
	}

	.container {
		height: 100%;
		display: grid;
		place-content: center;
	}

	h1 {
		font-size: 4rem;
	}

	ul {
		margin: 0;
		padding: 0;
		font-size: 2rem;
		list-style-position: inside;

		& a {
			color: hsl(213, 47%, 41%);
			text-decoration: none;
		}
	}
</style>