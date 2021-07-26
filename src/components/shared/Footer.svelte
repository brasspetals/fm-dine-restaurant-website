<script></script>

<footer>
  <div class="footer-content">
    <a href="/"><img class="footer__logo" src="./images/logo.svg/" alt="Dine - Home"></a>
    <div class="footer__text">
      <address>
        <p>Marthwaite, Sedbergh</p>
        <p>Cumbria</p>
        <a href="tel:+00 44 123 4567" class="tel">+00 44 123 4567</a> 
      </address>
      <div class="hours">
        <p>Open Times</p>
        <p>Mon - Fri: <span>09:00 AM - 10:00 PM</span></p>
        <p>Sat - Sun: <span>09:00 AM - 11:30 PM</span></p>
      </div>
    </div>
  </div>
</footer>

<style>
  footer {
    background-color: var(--color-soft-black);
    color: var(--color-white);
    padding: 5rem 1.5rem;
  }

  .footer-content {
    display: grid;
    justify-items: center;
    gap: 1.875rem;
  }

  .footer__logo {
    height: 2.5rem;
    width: auto;
  }

  .footer__text {
    display: grid;
    gap: 2rem;
    text-align: center;
  }

  address, p, .tel {
    font-style: normal;
    font-size: 0.875rem;
    font-weight: 400;
    line-height: 2;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  @media (max-width: 365px) {
    span {
      display: block;
    }
  }

  @media (min-width: 650px) { 
    footer {
      padding: 4rem 2.5rem;
    }

    .footer-content {
      grid-auto-flow: column;
      justify-content: start;
      gap: 130px;
    }

    .footer-content > a {
      align-self: start;
    }

    .footer__text {
      text-align: left;
    }
  }

  @media (min-width: 960px) {
    .footer-content {
      max-width: 1111px;
      margin: 0 auto;
      grid-template-columns: auto 1fr;
    }

    .footer__text {
      grid-auto-flow: column;
      justify-items: start;
      gap: 0;
      width: 100%;
    }
  }

  @media (min-width: 1150px) { 
    footer {
      padding: 4.875rem 4rem;
    }

    .footer-content {
      gap: 12.0625rem;
    }
  }
</style>