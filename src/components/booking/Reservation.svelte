<script>
  import Form from './Form.svelte'
</script>

<div class="reservation">
  <div class="content-container">
    <Form/>
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
  }
</style>