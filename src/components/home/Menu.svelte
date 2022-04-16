<script>
  import MenuList from './MenuList.svelte'
</script>

<section class="menu">
  <div class="menu__content">
    <div class="menu__heading">
      <img src="/images/patterns/pattern-divide.svg" alt="">
      <h2>A few highlights from our menu</h2>
      <p>We cater for all dietary requirements, but here’s a glimpse at some of our diner’s favourites. Our menu is revamped every season.</p>
    </div>
    <MenuList/>
  </div> 
</section>

<style>
  .menu {
    color: var(--color-white);
    background-color: var(--color-soft-black);
    display: grid;
    justify-items: center;
    padding: 4.5rem 1.5rem;
  }

  .menu__content {
    display: grid;
    justify-items: center;
    width: 100%;
    max-width: 69.4375rem;
    gap: 4rem;
  }

  .menu__heading {
    display: grid;
    justify-items: center;
    text-align: center;
  }

  .menu__heading img {
    margin-bottom: 2rem;
  }

  h2 {
    max-width: 12ch;
    margin-bottom: 1rem;
  }

  @media (min-width: 37.5rem) {
    .menu {
      padding: 6rem 2rem;
    }

    .menu__content {
      gap: 3.5rem;
    }
  }

  @media (min-width: 1050px) { 
    .menu {
      padding: 12.5625rem 4rem 4.0625rem;
      margin-top: -12.5rem;
    }
  }

  @media (min-width:1150px) {   
    .menu__content {
      grid-auto-flow: column;
      justify-content: space-between;
      grid-template-columns: 1fr 1fr;
      gap: 1.875rem;
    }

    .menu__heading {
      justify-items: start;
      align-content: start;
      text-align: left;
      width: 100%;
    }

    .menu__heading img {
      margin-bottom: 3rem;
    }
  }
</style>