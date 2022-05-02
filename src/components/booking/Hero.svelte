<script>
  import Logo from '../shared/Logo.svelte'
  import Button from '../shared/Button.svelte'

  let width
</script>

<svelte:window bind:innerWidth={width}/>

<header>
  <div class="header-wrapper">
    <Logo/>
    <div class="header__text">
      <h1>Reservations</h1>
      <p>We can’t wait to host you. If you have any special requirements please feel free to call on the phone number below. We’ll be happy to accommodate you.</p>
      {#if width < 600}
        <Button href="#form" text="Reserve Place"/>
      {/if}
    </div>
  </div>
</header>

<style>
  header {
    background-image: -webkit-image-set(
      url("/images/booking/hero-bg-mobile.jpg") 1x,
      url("/images/booking/hero-bg-mobile@2x.jpg") 2x);
    background-image: image-set(
      url("/images/booking/hero-bg-mobile.jpg") 1x,
      url("/images/booking/hero-bg-mobile@2x.jpg") 2x);
    background-repeat: no-repeat;
    background-position: top center;
    background-size: cover;
    height: 37.5rem;
    color: var(--color-white);
  }

  .header-wrapper { 
    padding: 3.5rem 1.5rem;
    text-align: center;
    display: grid;
    justify-items: center;
    align-content: start;
    gap: 2.5rem;
  }

  .header__text {
    display: grid;
    justify-items: center;
  }

  p {
    padding: 1rem 0 1.5rem;
  }

  @media screen and (min-width:37.5rem) {
    header {
      background-image: -webkit-image-set(
        url("/images/booking/hero-bg-tablet.jpg") 1x,
        url("/images/booking/hero-bg-tablet@2x.jpg") 2x);
      background-image: image-set(
        url("/images/booking/hero-bg-tablet.jpg") 1x,
        url("/images/booking/hero-bg-tablet@2x.jpg") 2x);
    }

    .header-wrapper { 
      padding: 3.5rem 2.4375rem;
      gap: 4rem;
    }

    :global(.header-wrapper > a) {
      justify-self: left;
    }

    p {
      max-width: 36ch;
    }
  }

  @media screen and (min-width: 71.875rem) {
    header {
      background-image: -webkit-image-set(
        url("/images/booking/hero-bg-desktop.jpg") 1x,
        url("/images/booking/hero-bg-desktop@2x.jpg") 2x);
      background-image: image-set(
        url("/images/booking/hero-bg-desktop.jpg") 1x,
        url("/images/booking/hero-bg-desktop@2x.jpg") 2x);
    }

    .header-wrapper {
      justify-items: left;
      text-align: left;
      max-width: 74.25rem;
      padding: 4.0625rem 2.4375rem;
      margin: 0 auto;
      gap: 9.5625rem;
    }

    .header__text {
      justify-items: left;
      max-width: 27.8125rem;
    }

    p {
      padding: 1.5rem 0;
    }
  }
</style>