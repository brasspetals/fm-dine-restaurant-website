<script>
	import {fly} from 'svelte/transition'
	import Hero from '../home/Hero.svelte'
	import About from '../home/About.svelte'
	import Menu from '../home/Menu.svelte'
	import Events from '../home/Events.svelte'
	import CTA from '../home/CTA.svelte'
	import Footer from '../shared/Footer.svelte'

	const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)')
  const reducedMotion = mediaQuery.matches
</script>

{#if reducedMotion}
	<div class="container">
		<Hero/>
		<main>
			<About/>
			<Menu/>
			<Events/>
			<CTA/>
		</main>
		<Footer/>
	</div>
{:else}
	<div class="container"  transition:fly={{delay: 200, duration: 1100, y: 5}}>
		<Hero/>
		<main>
			<About/>
			<Menu/>
			<Events/>
			<CTA/>
		</main>
		<Footer/>
	</div>
{/if}

<style>
  .container {
	 overflow-x: hidden;
 }

 main {
	 background-color: var(--color-white);
 }
</style>