<script>
  import {menu} from '../../../public/scripts/menu.js'
  import {reducedMotion} from '../../../public/scripts/stores'
  let y
  let width
</script>

<svelte:window bind:innerWidth={width} bind:scrollY={y}/>

{#if $reducedMotion || width < 1050}
  <ul class="menu__list">
    {#each menu as dish}
      <li class="dish " >
        <div class="dish__img">
          <picture>
            <source media="(min-width: 37.5rem)" srcset="{dish.tabletDesktopSrcset}">
            <img src={dish.src} srcset="{dish.mobileSrcset}" alt="">
          </picture>
        </div>
        <div class="dish__text">
          <h3>{dish.name}</h3>
          <p class="description">{dish.description}</p>
        </div>
      </li>
    {/each}
  </ul>
{:else}
  <ul class="menu__list" style="transform: translate(0,{(-y + 1700) / 10}px)">
  {#each menu as dish}
    <li class="dish " >
      <div class="dish__img">
        <picture>
          <source media="(min-width: 37.5rem)" srcset="{dish.tabletDesktopSrcset}">
          <img src={dish.src} srcset="{dish.mobileSrcset}" alt="">
        </picture>
      </div>
      <div class="dish__text">
        <h3>{dish.name}</h3>
        <p class="description">{dish.description}</p>
      </div>
    </li>
  {/each}
  </ul>
{/if}

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
    width: 100%;
  }

  .dish__text {
    display: grid;
    gap: 0.25rem;
  }

  .description {
    font-size: 0.9375rem;
    line-height: 1.8667;
    letter-spacing: -0.0119rem;
    max-width: 24ch;
  }

  .dish:not(:last-of-type) {
    border-bottom: 0.0625rem solid hsla(0, 0%, 100%, .15);
    padding-bottom: 1.5rem;
  }

  @media (min-width: 37.5rem) {
    .menu__list {
      text-align: left;
      justify-content: start;
      width: 100%;
      max-width: 35.9375rem;
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
      height: 0.0625rem;
      width: 2rem;
      right: -2rem;
      top: 1.125rem;
    }

    .dish__text {
      gap: 0;
    }

    h3 {
      margin-top: 0.3125rem;
    }

    .description {
      max-width: 28ch;
    }
  }

  @media (min-width: 65.625rem) { 
    .menu__list {
      padding: 3.4375rem 0;
    }
  }
</style>