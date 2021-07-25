<script>
  import MenuList from './MenuList.svelte'
</script>

<section class="menu">
  <div class="menu__content">
    <div class="menu__heading">
      <svg xmlns="http://www.w3.org/2000/svg" width="71" height="7"><g fill="none" fill-rule="evenodd"><path fill="#9E7F66" d="M15 3h56v1H15z"/><circle cx="3.5" cy="3.5" r="3" stroke="#9E7F66"/></g></svg>
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

  svg {
    margin-bottom: 32px;
  }

  h2 {
    max-width: 12ch;
    margin-bottom: 1rem;
  }

  p {
    max-width: 30ch;
  }


  @media (min-width: 37.5rem) {
    .menu {
      padding: 96px 2rem;
    }

    .menu__content {
      gap: 56px;
    }
  }
</style>