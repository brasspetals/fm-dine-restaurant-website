<script>
  import {menu} from '../../scripts/menu.js'
</script>

<div class="menu__list">
{#each menu as dish}
  <div class="dish">
    <div class="dish__img">
      <picture>
        <source media="(min-width: 37.5rem)" srcset="{dish.tabletDesktopSrcset}">
        <img srcset="{dish.mobileSrcset}" alt="">
      </picture>
    </div>
    <div class="dish__text">
      <h3>{dish.name}</h3>
      <p>{dish.description}</p>
    </div>
  </div>
{/each}
</div>

<style>
  .menu__list {
    display: grid;
    gap: 1.5rem;
    text-align: center;
  }

  .dish {
    display: grid;
    justify-items: center;
    gap: 2rem;
  }

  img {
    display: block;
    width: 100%;
  }

  .dish__text {
    display: grid;
    gap: 4px;
  }

  p {
    line-height: 1.8667;
    max-width: 24ch;
  }

  .dish:not(:last-of-type) {
    border-bottom: 1px solid hsla(0, 0%, 100%, .15);
    padding-bottom: 1.5rem;
  }
</style>