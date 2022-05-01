<script>
  import {events} from '../../../public/scripts/events.js'
  import Button from '../shared/Button.svelte'


  let y
  let width
  let activeItem = 'family'
  let activeTab = 'family'
  const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)')
  const reducedMotion = mediaQuery.matches
  let fadeout = false
  let fadein = false
  let hidden = false

  const selectEvent = function () {
    if (activeItem != this.id) {
      activeTab = this.id
      fadeout = true
      fadein = false
      hidden = true
      setTimeout(() => {
        activeItem = this.id
        hidden = false
        fadein = true
        fadeout = false
      }, 450);
    }  
  }


</script>

<svelte:window bind:innerWidth={width} bind:scrollY={y}/>

<section class="events">
    <div class="events-content-container">
    <div class="events__img">
      <div class="pattern-wrapper">
        <picture>
          <source media="(min-width: 71.875rem)" srcset={events[activeItem].desktopSrcset}>
          <source media="(min-width: 37.5rem)" srcset={events[activeItem].tabletSrcset}>
          {#if reducedMotion || width < 600}
            <img class="lg-img shadow" src={events[activeItem].src} srcset={events[activeItem].mobileSrcset} alt="" class:fadeout class:fadein class:hidden>
          {:else if width < 1150}
            <img style="transform: translate(0,{(-y + 3200) / 15}px)" class="lg-img shadow" src={events[activeItem].src} srcset={events[activeItem].mobileSrcset} alt="" class:fadeout class:fadein class:hidden>
          {:else}
            <img style="transform: translate(0,{(-y + 3100) / 13}px)" class="lg-img shadow" class:fadeout class:fadein class:hidden src={events[activeItem].src} srcset={events[activeItem].mobileSrcset} alt="">
          {/if}
        </picture>
        {#if reducedMotion || width < 600}
          <img src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {:else if width < 1150}
          <img style="transform: translate(0,{(-y + 3100) / 8}px)" src="/images/patterns/pattern-lines.svg" alt="" class="pattern"> 
        {:else}
          <img style="transform: translate(0,{(-y + 3000) / 8}px)" src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {/if}
      </div>
    </div>
    <div class="events-text-container">
      <div class="events__tabs">
        {#if reducedMotion}
          <button id="family" class="tab" class:active="{activeItem === 'family'}" on:click="{() => activeItem = 'family'}">Family Gathering</button>
          <button id="special" class="tab" class:active="{activeItem === 'special'}" on:click="{() => activeItem = 'special'}">Special Events</button>
          <button id="social" class="tab" class:active="{activeItem === 'social'}" on:click="{() => activeItem = 'social'}">Social Events</button>
        {:else}
          <button id="family" class="tab" class:active="{activeTab === 'family'}" on:click="{selectEvent}">Family Gathering</button>
          <button id="special" class="tab" class:active="{activeTab === 'special'}" on:click="{selectEvent}">Special Events</button>
          <button id="social" class="tab" class:active="{activeTab === 'social'}" on:click="{selectEvent}">Social Events</button>
        {/if}
      </div>
      <div class="events__text">
          <h2 class:fadeout class:fadein>{events[activeItem].type}</h2>
          <p class:fadeout class:fadein>{events[activeItem].description}</p>
          <Button black=true/>
      </div>
      </div>
  </div>
</section>

<style>
  .fadeout {
    animation: fadeOut .5s ease-out;
  }

  .fadein {
    animation: fadeIn .45s ease-in backwards;
    animation-delay: .2s;
  }

  .hidden {
    opacity: 0;
  }

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

  .lg-img {
    max-width: 100%;
    margin-bottom: 3rem;
  }

  .pattern {
    display: none;
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
    position: relative;
  }

  .tab:hover {
    opacity: 1;
  }

  .tab::after {
    content:'';
    position: absolute;
    height: 0.0625rem;
    width: 3rem;
    bottom: -0.0625rem;
    left: 50%;
    transform: translateX(-50%) scaleX(0);
    background-color:var(--color-brown);
    transition: all 1.15s ease;
  }

  @media (prefers-reduced-motion: reduce) {
    .tab::after {
      transition: none;
    }
  }

  .active.tab::after {
    transform: translateX(-50%) scaleX(1);
  }
  
  .active.tab {
    opacity: 1;
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

    .lg-img {
      margin-bottom: 3.5rem;
      position: relative;
    }

    .pattern-wrapper {
      position: relative;
      z-index: 1;
    }

    .pattern {
      display: block;
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

    .tab::after {
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

    .pattern {
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

    .tab::after {
      bottom: 47%;
      left: -4.9375rem;
      width: 6rem;
      z-index: 0;
      transform-origin: left;
    }
  }
</style>