<script>
	import {fly} from 'svelte/transition'
	import Hero from '../booking/Hero.svelte'
	import Reservation from '../booking/Reservation.svelte'
	import Footer from '../shared/Footer.svelte'

	const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)')
  const reducedMotion = mediaQuery.matches
</script>

{#if reducedMotion}
	<div class="container">
		<Hero/>
		<Reservation/>
		<Footer/>
	</div>
{:else}
	<div class="container" transition:fly={{delay: 200, duration: 1100, y: 5}}>
		<Hero/>
		<Reservation/>
		<Footer/>
	</div>
{/if}

<style>
  .container {
	 overflow-x: hidden;
 }
</style>
