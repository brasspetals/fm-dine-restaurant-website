<script>
	import Hero from '../home/Hero.svelte'
	import About from '../home/About.svelte'
	import Menu from '../home/Menu.svelte'
	import Events from '../home/Events.svelte'
	import CTA from '../home/CTA.svelte'
	import Footer from '../shared/Footer.svelte'
</script>

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

<style>
 .container {
	 overflow-x: hidden;
	 margin: 0 auto;
	 max-width: 93.75rem;
 }

 main {
	 background-color: var(--color-white);
 }
</style>