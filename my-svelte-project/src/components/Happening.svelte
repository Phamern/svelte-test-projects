<script>
  import {slide} from 'svelte/transition'
  let hei = 'heisann<h1>HEI</h1>'
  export let name
</script>

<main>
  	<div in:slide out:slide class="happening">
			<h2>It's happening {name}!</h2>	
		</div>
</main>

<style>

	.happening {
		position: fixed;
		top: 3rem;
		right: 3rem;
		padding: 2rem;
		background: lightblue;
		color: white;
	}

</style>