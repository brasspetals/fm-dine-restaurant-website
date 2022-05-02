<script>
  import {reducedMotion} from '../../../public/scripts/stores'
  let y
  let height
  let width
</script>

<svelte:window bind:innerWidth={width} bind:scrollY={y}/>

<section class="about" bind:offsetHeight={height}>
  <div class="about__content">
    <div class="about__img">
      <picture>
        <source media="(min-width: 65.625rem)" srcset="./images/homepage/enjoyable-place-desktop.jpg, ./images/homepage/enjoyable-place-desktop@2x.jpg 2x">
        <source media="(min-width: 37.5rem)" srcset="./images/homepage/enjoyable-place-tablet.jpg, ./images/homepage/enjoyable-place-tablet@2x.jpg 2x">
        {#if $reducedMotion || width < 600}
          <img class="lg-img top shadow" src="./images/homepage/enjoyable-place-mobile.jpg" srcset="./images/homepage/enjoyable-place-mobile.jpg, ./images/homepage/enjoyable-place-mobile@2x.jpg 2x" alt="">
        {:else if width < 1050}
          <img style="transform: translate(0,{(-y + 850) / 15}px)" class="lg-img top shadow" src="./images/homepage/enjoyable-place-mobile.jpg" srcset="./images/homepage/enjoyable-place-mobile.jpg, ./images/homepage/enjoyable-place-mobile@2x.jpg 2x" alt="">
        {:else}
          <img style="transform: translate(0,{(-y + 700) / 9}px)" class="lg-img top shadow" src="./images/homepage/enjoyable-place-mobile.jpg" srcset="./images/homepage/enjoyable-place-mobile.jpg, ./images/homepage/enjoyable-place-mobile@2x.jpg 2x" alt="">
        {/if}
      </picture>
    </div>
    <div class="about__text">
      <img src="/images/patterns/pattern-divide.svg" alt="">
      <h2>Enjoyable place for all the family</h2>
      <p>Our relaxed surroundings make dining with us a great experience for everyone. We can even arrange a tour of the farm before your meal.</p>
    </div>
  </div>
  <div class="about__content bottom">
    <div class="about__img">
      <div class="pattern-wrapper">
        <picture>
          <source media="(min-width: 65.625rem)" srcset="./images/homepage/locally-sourced-desktop.jpg, ./images/homepage/locally-sourced-desktop@2x.jpg 2x">
          <source media="(min-width: 37.5rem)" srcset="./images/homepage/locally-sourced-tablet.jpg, ./images/homepage/locally-sourced-tablet@2x.jpg 2x">
          {#if $reducedMotion || width < 600}
            <img class="lg-img shadow" src="./images/homepage/locally-sourced-mobile.jpg" srcset="./images/homepage/locally-sourced-mobile.jpg, ./images/homepage/locally-sourced-mobile@2x.jpg 2x" alt="">
          {:else if width < 1050}
            <img class="lg-img shadow" style="transform: translate(0,{(-y + height + 50) / 15}px)" src="./images/homepage/locally-sourced-mobile.jpg" srcset="./images/homepage/locally-sourced-mobile.jpg, ./images/homepage/locally-sourced-mobile@2x.jpg 2x" alt="">
          {:else}
            <img class="lg-img shadow" style="transform: translate(0,{(-y + height) / 9}px)" src="./images/homepage/locally-sourced-mobile.jpg" srcset="./images/homepage/locally-sourced-mobile.jpg, ./images/homepage/locally-sourced-mobile@2x.jpg 2x" alt="">
          {/if}
        </picture>
        {#if $reducedMotion || width < 600}
          <img src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {:else if width < 1050}
          <img style="transform: translate(0,{(-y + height) / 7}px)" src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {:else}
          <img style="transform: translate(0,{(-y + height) / 5}px)" src="/images/patterns/pattern-lines.svg" alt="" class="pattern">
        {/if}
      </div>
    </div>
    <div class="about__text">
      <img src="/images/patterns/pattern-divide.svg" alt="">
      <h2>The most locally sourced food</h2>
      <p>All our ingredients come directly from our farm or local fishery. So you can be sure that you’re eating the freshest, most sustainable food.</p>
    </div>
  </div>
</section>

<style>
  .about {
    display: grid;
    justify-items: center;
    padding: 0 1.5rem;
    position: relative;
  }
  
  .about__content {
    display: grid;
    justify-items: center;
    width: 100%;
    max-width: 69.4375rem;
    gap: 3rem;
    padding-bottom: 5rem;
  }

  .about__img {
    width: 100%;
    display: grid;
    justify-content: center;
  }

  .lg-img  { 
    position: relative;
    z-index: 1;
    max-width: 100%;
  }

  .top {
    margin-top: -4.5rem;
  }

  .pattern {
    display: none;
  }

  .about__text {
    display: grid;
    justify-items: center;
    text-align: center;
  }

  .about__text img {
    margin-bottom: 2rem;
  }

  h2 {
    max-width: 12ch;
    margin-bottom: 1rem;
  }

  @media (min-width: 37.5rem) {
    .about {
     position: relative;
    }

    .about::before {
      content: url("/images/patterns/pattern-curve-top-right.svg");
      position: absolute;
      top: 6.25rem;
      right: 51%;
    }

    .about::after {
      content: url("/images/patterns/pattern-curve-top-left.svg");
      position: absolute;
      bottom: -0.3125rem;
      left: 50%;
    }

    .about__content {
      gap: 3.5rem;
      padding-bottom: 7.5rem;
    }

    .about__text {
      position: relative;
      z-index: 1;
    }

    .top {
      margin-top: -6rem;
    }

    .pattern-wrapper {
      position: relative;
    }

    .pattern {
      display: block;
      position: absolute;
      top: 14.25rem;
      right: -3.625rem;
      z-index: 1;
    }
  }

  @media (min-width: 65.625rem) {
    .about {
      padding: 0 4rem;
    }

    .about::before {
      top: 15.625rem;
      right: unset;
      left: 0;
    }

    .about::after {
      bottom: 12.1875rem;
      left: unset;
      right: 0;
    }

    .about__content {
      grid-auto-flow: column;
      justify-content: space-between;
      grid-template-columns: minmax(40%, max-content) auto;
    }

    .top {
      margin-top: -4.375rem;
    }

    .bottom {
      grid-template-columns: auto minmax(40%, max-content);
    }
    
    .bottom > .about__img {
      order: 2;
    }

    .pattern {
      top: 17.6875rem;
      right: -7.125rem;
    }

    .lg-img  {
      width: 100%;
    }

    .about__img::before {
      top: 15.625rem;
      right: unset;
      left: 0;
    }

    .about__text {
      align-content:start;
      justify-items: left;
      text-align: left;
      max-width: 33ch;
      margin-top: 39.5%;
    }

    .bottom > .about__text {
      margin-top: 12.5rem;
    }

    h2 {
      min-width: 9ch;
    }

    .about__text img {
      margin-bottom: 3rem;
    }
  }
</style>