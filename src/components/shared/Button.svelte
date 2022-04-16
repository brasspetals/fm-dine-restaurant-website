<script>
  export let black = false
  export let href ="/book"
</script>

<a href="{href}" class:black={black}>Book a table</a>

<style>
  a {
    display: grid;
    justify-content: center;
    align-items: center;
    height: 4rem;
    width: 15.3125rem;
    background-color: transparent;
    border: 0.0625rem solid var(--color-white);
    font-size: 0.875rem;
    font-weight: 600;
    line-height: 1.143;
    letter-spacing: 0.125rem;
    text-transform: uppercase;
    transition: background-color .5s ease, color .5s ease;
  } 

  .black {
    background-color: var(--color-soft-black);
    border: 0.0625rem solid var(--color-soft-black);
    color: var(--color-white);
  }

  a:hover {
    color: var(--color-soft-black);
    background-color: var(--color-white);
    transition: background-color .5s ease, color .5s ease;
  }
</style>