<script>
  import {events} from '../../../public/scripts/events.js'
  import {reducedMotion} from '../../../public/scripts/stores'
  import Button from '../shared/Button.svelte'

  let y
  let width
  let activeItem = 'family'
  let activeTab = 'family'
  let fadeout = false
  let fadein = true

  const selectEvent = function () {
    if (activeItem != this.id) {
      activeTab = this.id
      fadein = false;
      fadeout = true
      setTimeout(() => {
        activeItem = this.id
        fadeout = false
        fadein = true
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
          <source media="(min-width: 71.875rem)" srcset={events["family"].desktopSrcset}>
          <source media="(min-width: 37.5rem)" srcset={events["family"].tabletSrcset}>
          {#if $reducedMotion || width < 600}
            <img class="lg-img shadow" src={events["family"].src} srcset={events["family"].mobileSrcset} alt="" class:fadeout class:fadein class:hide="{activeItem != 'family'}">
          {:else if width < 1150}
            <img style="transform: translate(0,{(-y + 3200) / 15}px)" class="lg-img shadow" src={events["family"].src} srcset={events["family"].mobileSrcset} alt="" class:fadeout class:fadein class:hide="{activeItem != 'family'}">
          {:else}
            <img style="transform: translate(0,{(-y + 3100) / 13}px)" class="lg-img shadow" class:fadeout class:fadein src={events["family"].src} srcset={events["family"].mobileSrcset} alt="" class:hide="{activeItem != 'family'}">
          {/if}
        </picture>
        <picture>
          <source media="(min-width: 71.875rem)" srcset={events["special"].desktopSrcset}>
          <source media="(min-width: 37.5rem)" srcset={events["special"].tabletSrcset}>
          {#if $reducedMotion || width < 600}
            <img class="lg-img shadow" src={events["special"].src} srcset={events["special"].mobileSrcset} alt="" class:fadeout class:fadein class:hide="{activeItem != 'special'}">
          {:else if width < 1150}
            <img style="transform: translate(0,{(-y + 3200) / 15}px)" class="lg-img shadow" src={events["special"].src} srcset={events["special"].mobileSrcset} alt="" class:fadeout class:fadein class:hide="{activeItem != 'special'}">
          {:else}
            <img style="transform: translate(0,{(-y + 3100) / 13}px)" class="lg-img shadow" class:fadeout class:fadein src={events["special"].src} srcset={events["special"].mobileSrcset} alt="" class:hide="{activeItem != 'special'}">
          {/if}
        </picture>
        <picture>
          <source media="(min-width: 71.875rem)" srcset={events["social"].desktopSrcset}>
          <source media="(min-width: 37.5rem)" srcset={events["social"].tabletSrcset}>
          {#if $reducedMotion || width < 600}
            <img class="lg-img shadow" src={events["social"].src} srcset={events["social"].mobileSrcset} alt="" class:fadeout class:fadein class:hide="{activeItem != 'social'}">
          {:else if width < 1150}
            <img style="transform: translate(0,{(-y + 3200) / 15}px)" class="lg-img shadow" src={events["social"].src} srcset={events["social"].mobileSrcset} alt="" class:fadeout class:fadein class:hide="{activeItem != 'social'}">
          {:else}
            <img style="transform: translate(0,{(-y + 3100) / 13}px)" class="lg-img shadow" class:fadeout class:fadein src={events["social"].src} srcset={events["social"].mobileSrcset} alt="" class:hide="{activeItem != 'social'}">
          {/if}
        </picture>
        {#if $reducedMotion || width < 600}
          <img src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {:else if width < 1150}
          <img style="transform: translate(0,{(-y + 3100) / 8}px)" src="/images/patterns/pattern-lines.svg" alt="" class="pattern"> 
        {:else}
          <img style="transform: translate(0,{(-y + 3000) / 8}px)" src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {/if}
      </div>
    </div>
    <div class="tab-text-wrapper">
      <div class="events__tabs">
        {#if $reducedMotion}
          <button id="family" class="tab" class:active="{activeItem === 'family'}" on:click="{() => activeItem = 'family'}" aria-selected="{activeItem === 'family'}">Family Gathering</button>
          <button id="special" class="tab" class:active="{activeItem === 'special'}" on:click="{() => activeItem = 'special'}" aria-selected="{activeItem === 'special'}">Special Events</button>
          <button id="social" class="tab" class:active="{activeItem === 'social'}" on:click="{() => activeItem = 'social'}" aria-selected="{activeItem === 'social'}">Social Events</button>
        {:else}
          <button id="family" class="tab" class:active="{activeTab === 'family'}" on:click="{selectEvent}" aria-selected="{activeTab === 'family'}">Family Gathering</button>
          <button id="special" class="tab" class:active="{activeTab === 'special'}" on:click="{selectEvent}" aria-selected="{activeTab === 'special'}">Special Events</button>
          <button id="social" class="tab" class:active="{activeTab === 'social'}" on:click="{selectEvent}" aria-selected="{activeTab === 'social'}">Social Events</button>
        {/if}
      </div>
      <div class="events__text" aria-live="polite">
        <div class="text-wrapper" class:hide="{activeItem != 'family'}" class:fadeout class:fadein>
          <h2>{events['family'].type}</h2>
          <p>{events['family'].description}</p>
        </div>
        <div class="text-wrapper" class:hide="{activeItem != 'special'}" class:fadeout class:fadein>
          <h2>{events['special'].type}</h2>
          <p>{events['special'].description}</p>
        </div>
        <div class="text-wrapper" class:hide="{activeItem != 'social'}" class:fadeout class:fadein>
          <h2>{events['social'].type}</h2>
          <p>{events['social'].description}</p>
        </div>
        <Button black=true/>
      </div>
      
    </div>
  </div>
</section>

<style>
  .hide {
    display: none;
  }

  .fadeout {
    animation: fadeOut .45s ease-out forwards;
  }

  .fadein {
    animation: fadeIn .45s .2s ease-in backwards;
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

  .tab-text-wrapper {
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
    transition: all 1s ease;
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
    margin-bottom: 1rem;
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

    .tab-text-wrapper {
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