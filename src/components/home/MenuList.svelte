<script>
  import {menu} from '../../scripts/menu.js'
</script>

<ul class="menu__list">
{#each menu as dish}
  <li class="dish">
    <div class="dish__img">
      <picture>
        <source media="(min-width: 37.5rem)" srcset="{dish.tabletDesktopSrcset}">
        <img srcset="{dish.mobileSrcset}" alt="">
      </picture>
    </div>
    <div class="dish__text">
      <h3>{dish.name}</h3>
      <p class="description">{dish.description}</p>
    </div>
  </li>
{/each}
</ul>

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

  .description {
    font-size: 0.9375rem;
    line-height: 1.8667;
    letter-spacing: -0.19px;
    max-width: 24ch;
  }

  .dish:not(:last-of-type) {
    border-bottom: 1px solid hsla(0, 0%, 100%, .15);
    padding-bottom: 1.5rem;
  }

  @media (min-width: 37.5rem) {
    .menu__list {
      text-align: left;
      justify-content: start;
      width: 100%;
      max-width: 575px;
    }

    .dish {
      grid-auto-flow: column;
      text-align: left;
      gap: 3.875rem;
      width: 100%;
    }

    .dish__img {
      position: relative;
    }

    .dish__img::after {
      content: '';
      background-color: var(--color-brown);
      position: absolute;
      height: 1px;
      width: 2rem;
      right: -2rem;
      top: 18px;
    }

    .dish__text {
      gap: 0;
    }

    h3 {
      margin-top: 5px;
    }

    .description {
      max-width: 28ch;
    }
  }
</style>