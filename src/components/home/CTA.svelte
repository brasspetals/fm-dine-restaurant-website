<script>
  import Button from '../shared/Button.svelte'
</script>

<section class="cta">
  <div class="cta__content">
    <h2>Ready to make a reservation?</h2>
    <Button/>
  </div>
</section>

<style>
  .cta {
    background-image: -webkit-image-set(
      url("/images/homepage/ready-bg-mobile.jpg") 1x,
      url("/images/homepage/ready-bg-mobile@2x.jpg") 2x);
    background-image: image-set(
      url("/images/homepage/ready-bg-mobile.jpg") 1x,
      url("/images/homepage/ready-bg-mobile@2x.jpg") 2x);
    background-repeat: no-repeat;
    background-size: cover;
    color: var(--color-white);
    text-align: center;
    display: grid;
    justify-items: center;
    padding: 5rem 1.5rem;
  }

  .cta__content {
    width: 100%;
    display: grid;
    gap: 1.5rem;
    justify-items: center;
    align-content: center;
  }

  h2 {
    color: var(--color-white);
  }

  @media (min-width: 37.5rem) { 
    .cta {
      background-image: -webkit-image-set(
        url("/images/homepage/ready-bg-tablet.jpg") 1x,
        url("/images/homepage/ready-bg-tablet@2x.jpg") 2x);
      background-image: image-set(
        url("/images/homepage/ready-bg-tablet.jpg") 1x,
        url("/images/homepage/ready-bg-tablet@2x.jpg") 2x);
      padding: 4rem 1.5rem;
    }
  }

  @media (min-width: 71.875rem) { 
    .cta {
      height: 15rem;
      padding: 4rem;
      background-image: -webkit-image-set(
        url("/images/homepage/ready-bg-desktop.jpg") 1x,
        url("/images/homepage/ready-bg-desktop@2x.jpg") 2x);
      background-image: image-set(
        url("/images/homepage/ready-bg-desktop.jpg") 1x,
        url("/images/homepage/ready-bg-desktop@2x.jpg") 2x);
    }

    .cta__content {
      max-width: 69.4375rem;
      grid-auto-flow: column;
      justify-content: space-between;
      align-items: center;
    }
  }
</style>