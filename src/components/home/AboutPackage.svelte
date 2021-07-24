<script>
  import { onMount } from 'svelte'
  import { Parallax, ParallaxLayer } from 'svelte-parallax'

  let prefersReducedMotion
  onMount(() => {
    prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches
  })
</script>

<section class="about-dine">
  <Parallax sections={2} disabled={prefersReducedMotion} style={"overflow: visible;  max-height: 450px;"}>
    <ParallaxLayer rate={.5} style={"display: grid; justify-items: center; width: 100%;"}>
      <img src="./images/homepage/enjoyable-place-mobile@2x.jpg" alt="">
    </ParallaxLayer>
  </Parallax>
  <div class="about__content">
    <h1>Exquisite dining since 1989</h1>
    <p>Experience our seasonal menu in beautiful country surroundings. Eat the freshest produce from the comfort of our farmhouse.</p>
  </div>
</section>

<style>
  .about-dine {
    display: grid;
    justify-items: center;
    padding: 0 1.5rem;
    width: 100%;
  }

  img { 
    margin-top: -72px;
    /* position: absolute;
    top: 0px; */
    width: 100%;
    max-width: 450px;
  }
</style>