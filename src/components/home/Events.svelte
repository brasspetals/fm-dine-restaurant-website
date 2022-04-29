<script>
  import {fade} from 'svelte/transition'
  import {sineInOut} from 'svelte/easing'
  import {events} from '../../../public/scripts/events.js'
  import Button from '../shared/Button.svelte'

  let activeItem = 'family'
</script>

<section class="events">
    <div class="events-content-container">
    <div class="events__img">
        <picture>
          <source media="(min-width: 65.625rem)" srcset={events[activeItem].desktopSrcset}>
          <source media="(min-width: 37.5rem)" srcset={events[activeItem].tabletSrcset}>
          <img class="shadow" in:fade={{delay: 650, duration:650, easing:sineInOut}} out:fade={{duration:650, easing:sineInOut}} src={events[activeItem].src} srcset={events[activeItem].mobileSrcset} alt="">
        </picture>
    </div>
    <div class="events-text-container">
      <div class="events__tabs">
        <button id="family" class="tab" class:active="{activeItem === 'family'}" on:click="{() => activeItem = 'family'}">Family Gathering</button>
        <button id="special" class="tab" class:active="{activeItem === 'special'}" on:click="{() => activeItem = 'special'}">Special Events</button>
        <button id="social" class="tab" class:active="{activeItem === 'social'}" on:click="{() => activeItem = 'social'}">Social Events</button>
      </div>
      <div class="events__text">
          <h2 in:fade={{delay: 650, duration:650, easing:sineInOut}} out:fade={{duration:650, easing:sineInOut}}>{events[activeItem].type}</h2>
          <p in:fade={{delay: 650, duration:650, easing:sineInOut}} out:fade={{duration:650, easing:sineInOut}}>{events[activeItem].description}</p>
          <Button black=true/>
      </div>
      </div>
  </div>
</section>

<style>
  .events {
    padding: 5rem 1.5rem 7.75rem;
  }

  .events-content-container {
    display: grid;
    justify-items: center;
    width: 100%;
    max-width: 69.375rem;
    margin: 0 auto;
  }

  .events__img img {
    max-width: 100%;
    margin-bottom: 3rem;
  }

  .events-text-container {
    display: grid;
    width: 100%;
    justify-items: center;
  }

  .events__tabs {
    display: grid;
    gap: 1rem;
    margin-bottom: 1.5rem;
  }

  .tab {
    background-color: transparent;
    font-weight: 600;
    font-size: 0.875rem;
    line-height: 2;
    letter-spacing: 0.125rem;
    text-transform: uppercase;
    color: #4C4C4C;
    opacity: .5;
    transition: opacity .5s ease;
  }

  .tab:hover {
    opacity: 1;
  }
  
  .active {
    opacity: 1;
    position: relative;
  }

  .active::after {
    content:'';
    position: absolute;
    height: 0.0625rem;
    width: 3rem;
    bottom: -0.0625rem;
    left: 50%;
    transform: translateX(-50%);
    background-color:var(--color-brown);
  }

  .events__text {
    display: grid;
    text-align: center;
    justify-items: center;
    gap: 1rem;
  }

  h2 {
    text-transform: capitalize;
  }

  p {
    margin-bottom: 1rem;
  }

  @media screen and (min-width: 37.5rem) {
    .events {
      padding: 7.5rem 2.4375rem;
      position: relative;
    }

    .events::before {
      content: url("/images/patterns/pattern-curve-top-right.svg");
      position: absolute;
      top: 0;
      right: 51%;
    }

    .events__img img {
      margin-bottom: 3.5rem;
    }

    .events__img > picture {
      position: relative;
      z-index: 1;
    }

    .events__img > picture::after {
      content: url("/images/patterns/pattern-lines.svg");
      position: absolute;
      top: -1.5rem;
      left: -3.625rem;
    }

    .events__tabs {
      grid-auto-flow: column;
      width: 100%;
      justify-content: space-between;
      max-width: 40.75rem;
      gap: unset;
      margin-bottom: 3.0625rem;
    }

    .active::after {
      bottom: -0.5625rem;
    }
  }

  @media screen and (min-width: 71.875rem) { 
    .events {
      padding: 10rem 2.4375rem 6.5rem;
    }

    .events::before {
      right: unset;
      left: -21.875rem;
    }

    .events-content-container {
      justify-content: space-between;
      grid-auto-flow: column;
    }

    .events__img > picture::after {
      left: -2.5rem;
    }

    .events-text-container {
      max-width: 27.75rem;
      align-content: start;
      gap: 0.8125rem;
    }

    .events__text {
      padding: 4rem 0;
      justify-items: left;
      text-align: left;
      align-content: start;
    }

    .events__tabs {
      grid-auto-flow: row;
      gap: 0.75rem;
      align-content: start;
      justify-items: start;
      margin-bottom: unset;
      order: 2;
    }

    .active::after {
      bottom: 47%;
      left: -4.9375rem;
      width: 6rem;
      z-index: 0;
    }
  }
</style>