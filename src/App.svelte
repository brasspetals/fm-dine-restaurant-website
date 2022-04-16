<script>
	import Hero from './components/home/Hero.svelte'
	import About from './components/home/About.svelte'
	import Menu from './components/home/Menu.svelte'
	import Events from './components/home/Events.svelte'
	import CTA from './components/home/CTA.svelte'
	import Footer from './components/shared/Footer.svelte'
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