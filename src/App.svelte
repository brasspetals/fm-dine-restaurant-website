<script>
	import Hero from './components/home/Hero.svelte'
	import About from './components/home/About.svelte'
	import Menu from './components/home/Menu.svelte'
	import CTA from './components/home/CTA.svelte'
	import Footer from './components/shared/Footer.svelte'
</script>

<Hero/>
<About/>
<Menu/>
<div class="break"></div>
<CTA/>
<Footer/>

<style>
	.break {
		background-color: white;
		height: 1044px;
		width: 100%;
	}
</style>