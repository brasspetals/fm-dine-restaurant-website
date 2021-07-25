<script></script>

<section class="about">
  <div class="about__content">
    <div class="about__img">
      <picture>
        <source media="(min-width: 1150px)" srcset="./images/homepage/enjoyable-place-desktop.jpg, ./images/homepage/enjoyable-place-desktop@2x.jpg 2x">
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
  <div class="about__content even">
    <div class="about__img">
      <picture>
        <source media="(min-width: 1150px)" srcset="./images/homepage/locally-sourced-desktop.jpg, ./images/homepage/locally-sourced-desktop@2x.jpg 2x">
        <source media="(min-width: 37.5rem)" srcset="./images/homepage/locally-sourced-tablet.jpg, ./images/homepage/locally-sourced-tablet@2x.jpg 2x">
        <img srcset="./images/homepage/locally-sourced-mobile.jpg, ./images/homepage/locally-sourced-mobile@2x.jpg 2x" alt="">
      </picture>
    </div>
    <div class="about__text">
      <svg xmlns="http://www.w3.org/2000/svg" width="71" height="7"><g fill="none" fill-rule="evenodd"><path fill="#9E7F66" d="M15 3h56v1H15z"/><circle cx="3.5" cy="3.5" r="3" stroke="#9E7F66"/></g></svg>
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
    gap: 48px;
    padding-bottom: 80px;
  }

  .about__img {
    width: 100%;
    display: grid;
    justify-content: center;
  }

  img { 
    display: block;
    position: relative;
    z-index: 1;
    box-shadow: 0rem 3rem 5rem -50px rgba(0, 0, 0, .75);
    max-width: 100%;
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
    .about {
     position: relative;
    }

    .about::before {
      content: url("/images/patterns/pattern-curve-top-right.svg");
      position: absolute;
      top: 100px;
      right: 51%;
    }

    .about::after {
      content: url("/images/patterns/pattern-curve-top-left.svg");
      position: absolute;
      bottom: -5px;
      left: 50%;
    }

    .about__content {
      gap: 56px;
      padding-bottom: 120px;
    }

    .top {
      margin-top: -96px;
    }
  }

  @media (min-width: 740px) {
    .even * picture {
      position: relative;
    }

    .even * picture::after {
      content: url("/images/patterns/pattern-lines.svg");
      position: absolute;
      top: 228px;
      right: -58px;
      z-index: 1;
    }
  }

  @media (min-width: 1150px) {
    .about {
      padding: 0 4rem;
    }

    .about::before {
      top: 250px;
      right: unset;
      left: 0;
    }

    .about::after {
      bottom: 195px;
      left: unset;
      right: 0;
    }

    .about__content {
      grid-auto-flow: column;
      justify-content: space-between;
      grid-template-columns: minmax(40%, max-content) auto;
    }

    .top {
      margin-top: -70px;
    }

    .even {
      grid-template-columns: auto minmax(40%, max-content);
    }
    
    .even > .about__img {
      order: 2;
    }

    .even * picture::after {
      top: 283px;
      right: -114px;
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
      align-content:start;
      justify-items: left;
      text-align: left;
      max-width: 33ch;
      /* align-self: center;
      margin-top: -5.5%; */
      margin-top: 39.5%;
    }

    .even > .about__text {
      margin-top: 200px;
    }

    h2 {
      min-width: 9ch;
    }

    svg {
    margin-bottom: 48px;
  }
  }
</style>