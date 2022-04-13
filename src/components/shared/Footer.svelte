<script>
  import Logo from './Logo.svelte'
</script>

<footer>
  <div class="footer-content">
    <Logo footer=true/>
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
    gap: 2.5rem;
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
    letter-spacing: 0.125rem;
    text-transform: uppercase;
  }

  .tel {
    transition: color .5s ease;
  }

  .tel:hover {
    color: var(--color-brown);
  }

  @media (max-width: 22.8125rem) {
    span {
      display: block;
    }
  }

  @media (min-width: 40.625rem) { 
    footer {
      padding: 4rem 2.5rem;
    }

    .footer-content {
      grid-auto-flow: column;
      justify-content: start;
      gap: 8.125rem;
    }

    .footer__text {
      text-align: left;
    }
  }

  @media (min-width: 60rem) {
    .footer-content {
      max-width: 69.6875rem;
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

  @media (min-width: 71.875rem) { 
    footer {
      padding: 4.8125rem 4rem;
    }

    .footer-content {
      gap: 11.875rem;
    }
  }
</style>