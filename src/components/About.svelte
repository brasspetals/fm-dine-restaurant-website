<script></script>

<section class="about">
  <div class="about__content">
    <div class="about__img">
      <picture>
        <source media="(min-width: 1000px)" srcset="./images/homepage/enjoyable-place-desktop.jpg, ./images/homepage/enjoyable-place-desktop@2x.jpg 2x">
        <source media="(min-width: 37.5rem)" srcset="./images/homepage/enjoyable-place-tablet.jpg, ./images/homepage/enjoyable-place-tablet@2x.jpg 2x">
        <img class="top" srcset="./images/homepage/enjoyable-place-mobile.jpg, ./images/homepage/enjoyable-place-mobile@2x.jpg 2x" alt="">
      </picture>
    </div>
    <div class="about__text">
      <svg xmlns="http://www.w3.org/2000/svg" width="71" height="7"><g fill="none" fill-rule="evenodd"><path fill="#9E7F66" d="M15 3h56v1H15z"/><circle cx="3.5" cy="3.5" r="3" stroke="#9E7F66"/></g></svg>
      <h2>Enjoyable place for all the family</h2>
      <p>Our relaxed surroundings make dining with us a great experience for everyone. We can even arrange a tour of the farm before your meal.</p>
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
    gap: 48px;
    margin-bottom: 80px;
  }

  .about__img {
    width: 100%;
    display: grid;
    justify-content: center;
  }

  img { 
    display: block;
    /* width: 100%; */
    position: relative;
    z-index: 1;
    box-shadow: 0rem 3rem 5rem -50px rgba(0, 0, 0, .75);
  }

  .top {
    margin-top: -72px;
  }

  .about__text {
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
    .about__content {
      gap: 56px;
    }

    .about__img::before {
      content: url("/images/patterns/pattern-curve-top-right.svg");
      position: absolute;
      top: 100px;
      right: 51%;
    }

    .top {
      margin-top: -96px;
    }
  }

  @media (min-width: 1000px) {
    .about {
      padding: 0 4rem;
    }

    .about__content {
      grid-auto-flow: column;
      /* grid-template-columns: 50% 1fr; */
      /* gap: 125px; */
      justify-content: space-between;
    }

    .top {
      margin-top: -70px;
    }

    img {
      width: 100%;
    }

    .about__img::before {
      top: 250px;
      right: unset;
      left: 0;
    }

    .about__text {
      padding-top: 177px;
      align-content:start;
      justify-items: left;
      text-align: left;
      max-width: 33ch;
    }

    p {
      /* max-width: 33ch; */
    }

    svg {
    margin-bottom: 48px;
  }
  }
</style>