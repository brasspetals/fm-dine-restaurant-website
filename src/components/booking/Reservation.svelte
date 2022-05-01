<script>
  import Form from './Form.svelte'

  let width
  let y
  const mediaQuery = window.matchMedia('(prefers-reduced-motion: reduce)')
  const reducedMotion = mediaQuery.matches
</script>

<svelte:window bind:innerWidth={width} bind:scrollY={y}/>

<div class="reservation">
  <div class="content-container">
    <div class="pattern-wrapper">
      <Form/>
      {#if reducedMotion || width < 1050}
        <img src="/images/patterns/pattern-lines.svg" alt="">
      {:else}
        <img style="transform: translate(0,{-y / 11}px)" src="/images/patterns/pattern-lines.svg" alt="">
      {/if}
    </div>
  </div>
</div>


<style>
  .reservation {
    height: 33.375rem;
    margin: 0 auto;
    background-color: var(--color-white);
  }

  .content-container {
    padding: 0 1.5rem;
    width: 100%;
  }

  .pattern-wrapper {
    transform: translateY(-8.5625rem);
  }

  .pattern-wrapper > img {
    display: none;
  }

  @media screen and (min-width: 37.5rem) {
    .pattern-wrapper {
      transform: translateY(-14.375rem);
    }
  }

  @media screen and (min-width: 71.875rem) {
    .reservation {
      height: 20rem;
      background-image: url('/images/patterns/pattern-curve-bottom-right.svg');
      background-repeat: no-repeat;
      background-position: top left;
    }

    .content-container {
      max-width: 1158px;
      margin: 0 auto;
      display: grid;
      justify-content: end;
      align-content: start;
    }

    .pattern-wrapper {
      transform: translateY(-21.375rem);
      position: relative;
      z-index: 1;
    }

    .pattern-wrapper > img {
      display: block;
      position: absolute;
      left: -5rem;
      bottom: -2.6875rem;
      z-index: -1;
    }
  }
</style>