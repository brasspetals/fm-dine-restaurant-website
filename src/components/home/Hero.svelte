<script>
  import Logo from '../shared/Logo.svelte'
  import Button from '../shared/Button.svelte';
</script>

<header class="hero">
  <div class="hero__content">
    <Logo/>
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
    background-size: cover;
    color: var(--color-white);
    text-align: center;
    padding: max(14.5rem, 61.87%) 1.5rem 9.5rem;
  }

  .hero__content {
    width: 100%;
    max-width: 69.375rem;
  }

  .hero__text {
    display: grid;
    justify-items: center;
    padding-top: 2rem;
  }

  h1 { 
    max-width: 10ch;
  }

  p {
    padding: 1.5rem 0 2rem;
  }

  @media (min-width: 37.5rem) {
    .hero {
      background-image: -webkit-image-set(
        url("/images/homepage/hero-bg-tablet.jpg") 1x,
        url("/images/homepage/hero-bg-tablet@2x.jpg") 2x);
      background-image: image-set(
        url("/images/homepage/hero-bg-tablet.jpg") 1x,
        url("/images/homepage/hero-bg-tablet@2x.jpg") 2x);
      padding: max(23.375rem, 48.7%) 1.5rem 13.5rem;
    }

    p { 
      padding: 1.5rem 0;
      max-width: 36ch;
    }
  }

  @media (min-width: 65.625rem) {
    .hero {
      background-image: -webkit-image-set(
        url("/images/homepage/hero-bg-desktop.jpg") 1x,
        url("/images/homepage/hero-bg-desktop@2x.jpg") 2x);
      background-image: image-set(
        url("/images/homepage/hero-bg-desktop.jpg") 1x,
        url("/images/homepage/hero-bg-desktop@2x.jpg") 2x);
      padding: 4.0625rem 4rem 4rem;
      text-align: left;
      display: grid;
      justify-items: center;
      min-height: 51.25rem;
    }

    .hero__text {
      justify-items: left;
      padding-top: 9.5rem;
    }

    p {
      padding: 1.5rem 0 2.625rem;
      max-width: 30ch;
    }
  }
</style>