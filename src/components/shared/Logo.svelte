<script>
  export let footer = false;
</script>

<a href="/"><img class="logo" class:footer={footer} src="./images/logo.svg/" alt="Dine - Home"></a>

<style>
  .logo {
    height: 2rem;
    width: auto;
    margin: 0 auto;
  }

  .footer {
    height: 2.5rem;
  }

  @media (min-width: 37.5rem) {
    .logo {
      height: 2.5rem;
    }

    a {
      align-self: start;
    }
  }

  @media (min-width: 65.625rem) {
    .logo {
      margin: 0.0625rem 0.1875rem 0;
    }
  }
</style>