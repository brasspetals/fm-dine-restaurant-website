<script>
  import Button from '../components/Button.svelte';
</script>

<header class="hero">
  <a href="/"><img class="hero__logo" src="./images/logo.svg/" alt="Dine - Home"></a>
  <div class="hero__content">
    <h1>Exquisite dining since 1989</h1>
    <p>Experience our seasonal menu in beautiful country surroundings. Eat the freshest produce from the comfort of our farmhouse.</p>
    <Button/>
  </div>
  
</header>

<style>
  .hero {
    background-color: var(--color-soft-black);
    background-image: -webkit-image-set(
      url("/images/homepage/hero-bg-mobile.jpg") 1x,
      url("/images/homepage/hero-bg-mobile@2x.jpg") 2x);
    background-image: image-set(
      url("/images/homepage/hero-bg-mobile.jpg") 1x,
      url("/images/homepage/hero-bg-mobile@2x.jpg") 2x);
    background-repeat: no-repeat;
    background-position: top center;
    color: var(--color-white);
    text-align: center;
    padding: 14.5rem 1.5rem 9.5rem;
  }

  .hero__logo {
    height: 2rem;
    width: auto;
    margin-bottom: 1.6875rem;
  }

  .hero__content {
    display: grid;
    justify-items: center;
  }

  h1 { 
    max-width: 10ch;
  }

  p {
    padding: 1.5rem 0 2rem;
    max-width: 36ch;
  }

  @media (min-width: 37.5rem) {
    .hero {
      background-image: -webkit-image-set(
        url("/images/homepage/hero-bg-tablet.jpg") 1x,
        url("/images/homepage/hero-bg-tablet@2x.jpg") 2x);
      background-image: image-set(
        url("/images/homepage/hero-bg-tablet.jpg") 1x,
        url("/images/homepage/hero-bg-tablet@2x.jpg") 2x);
      background-size: cover;
      padding: 23.375rem 1.5rem 13.5rem;
    }

    .hero__logo {
      height: 2.5rem;
    }

    p { 
      padding: 1.5rem 0;
    }
  }
</style>