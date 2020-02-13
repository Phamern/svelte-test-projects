<script>
	import Parallax from 'parallax-js'
	import {slide} from 'svelte/transition'

	let info = ''

	let backImage = './images/human.png'

	let infoBox = (i) => {
		if( i === 3 ) {
			return true
		}
	}

	let images = [
		'./images/solnedgang_ørken.png',
		'./images/moon.png',
		'./images/landscape.png',
		'./images/human.png'
		// 'https://image.flaticon.com/icons/svg/119/119596.svg', 
		// 'https://image.flaticon.com/icons/svg/789/789395.svg', 
		// 'https://image.flaticon.com/icons/svg/414/414927.svg', 
		// 'https://image.flaticon.com/icons/svg/789/789392.svg'
	]

	let parallaxInstance
	const ready = node => {
		parallaxInstance = new Parallax(node)
		parallaxInstance.scalar(20.0)
		parallaxInstance.invert(false, false)
	}

</script>

<main>
	<section>
		<!-- <img src='{backImage}' class='backImage' alt='Background' /> -->
		<div use:ready>
			{#each images as image, i}
				<div data-depth='{i + .2}'>
					<img on:click={() => infoBox(i)} src='{image}' alt='parallax'class='image{[i]}' />
				</div>
			{/each}
		</div>
	</section>
		<h1 on:click={() =>  info = !info } class='clickinfo'>Info</h1>
	<section>
		{#if info}
	<section in:slide out:slide class='fixed'>
		<div>This is awesome</div>
	</section>
		{/if}
	</section>
		
</main>

<style>

:global(*) {
	box-sizing: border-box;
}

:global(html, body) {
	margin: 0;
	padding: 0;
}

	main {
		display: grid;
		height: 100vh;
		width: 100vw;
		place-items: end;
		overflow: hidden;
		position: relative;
	}

	.backImage {
		z-index: 10;
		position: absolute;
		top: 70vh;
	}

	.image0 {
		/* width: 40vw; */
		width: 150vw;
		height: 150vh;
		margin-left: -20vw;
		margin-top: -20vh;

	}
	.image1 {
		width: 40vw;
		margin-top: 20vh;
		/* width: 20vw;
		margin: -2vh 0 0 16vw; */
	}
	.image2 {
		width: 200vw;
		margin-top: 70vh;
		margin-left: -60vw;
	}
	.image3 {
		width: 20vw;
		margin-top: 70vh;
	}

	.clickinfo {
		cursor: pointer;
	}

	section {
		display: grid;
		place-items: center;
		font-size: 4rem;
	}

	.fixed {
		width: 30rem;
		height: 40rem;
		background-color: lightblue;
		position: fixed;
		top: 0;
		right: 0;
		color: white;
	}

</style>