<script>
  import Button from '../components/Button.svelte';
</script>

<header class="hero">
  <div class="hero__content">
    <a href="/"><img class="hero__logo" src="./images/logo.svg/" alt="Dine - Home"></a>
    <div class="hero__text">
      <h1>Exquisite dining since 1989</h1>
      <p>Experience our seasonal menu in beautiful country surroundings. Eat the freshest produce from the comfort of our farmhouse.</p>
      <Button/>
    </div>
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

  .hero__content {
    width: 100%;
    max-width: 69.4375rem;
  }

  .hero__logo {
    height: 2rem;
    width: auto;
    margin-bottom: 1.6875rem;
  }

  .hero__text {
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

  @media (min-width: 53.125rem) {
    .hero {
      background-image: -webkit-image-set(
        url("/images/homepage/hero-bg-desktop.jpg") 1x,
        url("/images/homepage/hero-bg-desktop@2x.jpg") 2x);
      background-image: image-set(
        url("/images/homepage/hero-bg-desktop.jpg") 1x,
        url("/images/homepage/hero-bg-desktop@2x.jpg") 2x);
      background-size: cover;
      padding: 4rem;
      text-align: left;
      display: grid;
      justify-items: center;
      min-height: 51.25rem;
    }

    .hero__logo {
      margin: 0.0625rem 0.1875rem 9.25rem;
    }

    .hero__text {
      justify-items: left;
    }

    p {
      max-width: 30ch;
      padding: 1.5rem 0 2.625rem;
    }
  }
</style>